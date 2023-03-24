![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
***
- [Authentication](#authentication)
    - [Request authorization token and run commands](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#request-authorization-token-and-run-a-command)
    - [Authorize and run commands in member CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#authorize-and-run-commands-across-member-cids-within-a-script)
- [Ingesting data](#ingesting-data)
    - [Retrieve items from a text file or CSV](#retrieve-items-from-a-text-file-or-csv)
    - [Retrieve identifiers using a list](#retrieve-identifiers-using-a-list)
- [Manipulating objects](#manipulating-objects)
    - [Add properties to an object](#add-properties-to-an-object)
    - [Iterate properties of an object](#iterate-properties-of-an-object)
***
# Authentication
## Request authorization token and run commands
This content has been moved to https://github.com/CrowdStrike/psfalcon/wiki/Authentication#request-authorization-token-and-run-a-command
## Authorize and run commands in member CIDs
This content has been moved to https://github.com/CrowdStrike/psfalcon/wiki/Authentication#authorize-and-run-commands-across-member-cids-within-a-script
# Ingesting data
## Retrieve items from a text file or CSV
Collect a list of items (identifiers, hostnames, group names, etc.) from a text file, exclude blank values and
save to the variable `$List`, which can be used with a PSFalcon command.
```powershell
#Requires -Version 5.1
param(
    [Parameter(Mandatory)]
    [ValidateScript({
        if (Test-Path -Path $_ -PathType Leaf) {
            $true
        } else {
            throw "Cannot find path '$_' because it does not exist or is a directory."
        }
    })]
    [string]$Path
)
[string]$FilePath = if (![IO.Path]::IsPathRooted($PSBoundParameters.Path)) {
    $FullPath = Join-Path (Get-Location).Path $PSBoundParameters.Path
    $FullPath = Join-Path $FullPath '.'
    [IO.Path]::GetFullPath($FullPath)
} else {
    $PSBoundParameters.Path
}
[string[]]$List = @((Get-Content -Path $FilePath).Normalize()).foreach{ if (![string]::IsNullOrEmpty($_)) { $_ }}
```
Collecting a list of hostnames (using the column `Hostname`) from a CSV can be done by modifying the
`$List` line.
```powershell
[string[]]$List = ((Import-Csv -Path $FilePath).Hostname).foreach{ if (![string]::IsNullOrEmpty($_)) { $_ }}
```
## Retrieve identifiers using a list
The `Filter` parameter \(a Falcon Query Language statement\) will accept a limited number of conditions at a
time. If you have a list of hostnames that you need to match with their identifiers, you can use the
[Find-FalconHostname](Find-FalconHostname) command.
```powershell
(Get-Content -Path $FilePath).Normalize() | Find-FalconHostname
```
# Manipulating Objects
## Add properties to an object
Most PSFalcon commands return `[PSCustomObject]` results. One of the [fastest ways](https://ramblingcookiemonster.github.io/Decorating-Objects/) to add
properties to a `[PSCustomObject]` can be converted into a simple function that you can re-use.
```powershell
#Requires -Version 5.1
function Set-Property {
    [CmdletBinding()]
    [OutputType([void])]
    param([object]$Object,[string]$Name,[object]$Value)
    process {
        if ($Object.$Name) {
            # Update existing property
            $Object.$Name = $Value
        } else {
            # Add property to [PSCustomObject]
            $Object.PSObject.Properties.Add((New-Object PSNoteProperty($Name,$Value)))
        }
    }
}
```
For example, if you wanted to add property `test` with value `abc` to a `Get-FalconHost` result:
```powershell
$HostObject = Get-FalconHost -Filter "hostname:'EXAMPLE-PC'" -Detailed
Set-Property -Object $HostObject -Name 'test' -Value 'abc'
```
## Iterate properties of an object
Different types of objects require different methods to figure out what properties are available in an object.
Most PSFalcon command results are arrays of `[PSCustomObject]` values, which allows manipulation in several
different ways, but they're not always easy to understand to someone inexperienced with PowerShell.

It's easiest to start with your result saved to a variable:
```powershell
$HostList = Get-FalconHost -Detailed
```
From there, you can use `Select-Object` to choose certain properties:
```powershell
$HostList | Select-Object device_id,hostname,local_ip

device_id   hostname     local_ip
---------   --------     --------
<redacted>  EXAMPLE-PC1  192.168.0.10
<redacted>  EXAMPLE-PC2  192.168.0.11

```
`Where-Object` can be used to filter for results with specific properties, using an exact match, or a RegEx match:
```powershell
$HostList | Where-Object { $_.hostname -eq 'EXAMPLE-PC2' } | Select-Object device_id,hostname,local_ip

device_id   hostname     local_ip
---------   --------     --------
<redacted>  EXAMPLE-PC2  192.168.0.11

$HostList | Where-Object { $_.hostname -match 'PC2' } | Select-Object device_id,hostname,local_ip

device_id   hostname     local_ip
---------   --------     --------
<redacted>  EXAMPLE-PC2  192.168.0.11
```
`Group-Object` can help determine counts, like devices by `agent_version`, or devices by `os_version`:
```powershell
$HostList | Group-Object agent_version

Count Name                      Group
----- ----                      -----
    2 6.26.14003.0              {@{device_id=...

$HostList | Group-Object os_version

Count Name                      Group
----- ----                      -----
    2 Windows 10                {@{device_id=...
```
Things become more complex when you don't know what properties are available, and it can be made more difficult
when those properties aren't part of the object. For example, the Falcon APIs will omit properties when they
aren't present, like when a device is not joined to a domain:
```powershell
$HostList | Select-Object device_id,hostname,machine_domain

device_id   hostname     machine_domain
---------   --------     --------
<redacted>  EXAMPLE-PC1  
<redacted>  EXAMPLE-PC2  example.com
```
To determine the number of properties that are present on both objects, it's easy to count the array itself.
Unfortunately, PowerShell will only display the properties of the first object in the array. Properties for each
object are only displayed when checking each object individually:
```powershell
($HostList | Get-Member | Where-Object { $_.MemberType -eq 'NoteProperty' }).Count
42

$HostList | ForEach-Object { ($_ | Get-Member | Where-Object { $_.MemberType -eq 'NoteProperty' }).Count }
42
45
```
Checking each object for the property names, then grouping them and selecting the unique properties can provide a
list of the available property names across all objects in the array:
```powershell
($HostList | ForEach-Object { ($_ | Get-Member | Where-Object { $_.MemberType -eq 'NoteProperty' }).Name } | Group-Object).Name
agent_load_flags
agent_local_time
agent_version
...
```