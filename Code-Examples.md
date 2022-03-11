![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
***
The examples provided below are for example purposes only and are offered 'as is' with no support.
***
### Authentication
* [Request authorization token and run commands](#request-authorization-token-and-run-commands)
* [Authorize and run commands in member CIDs](#authorize-and-run-commands-in-member-cids)
### Ingesting Data
* [Retrieve items from a text file or CSV](#retrieve-items-from-a-text-file-or-csv)
* [Retrieve identifiers using a list](#retrieve-identifiers-using-a-list)
### Manipulating Objects
* [Add properties to an object](#add-properties-to-an-object)
* [Iterate properties of an object](#iterate-properties-of-an-object)
***
# Authentication
## Request authorization token and run commands
An example of how to include OAuth2 API Client information as parameters and perform an authorization token request to the associated CID or "member" CID.
```powershell
#Requires -Version 5.1
using module @{ ModuleName = 'PSFalcon'; ModuleVersion = '2.0' }
[CmdletBinding()]
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $ClientId,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{40}$')]
    [string] $ClientSecret,

    [Parameter()]
    [ValidateSet('us-1', 'us-2', 'us-gov-1', 'eu-1')]
    [string] $Cloud,

    [Parameter()]
    [ValidatePattern('^\w{32}$')]
    [string] $MemberCid
)
begin {
    $TokenParam = @{}
    @('ClientId', 'ClientSecret', 'Cloud', 'MemberCid').foreach{
        if ($PSBoundParameters.$_) {
            $TokenParam[$_] = $PSBoundParameters.$_
        }
    }
}
process {
    try {
        Request-FalconToken @TokenParam
        # Insert code to run and output data here
    } catch {
        throw $_
    } finally {
        if ((Test-FalconToken).Token -eq $true) {
            Revoke-FalconToken
        }
    }
}
```
## Authorize and run commands in member CIDs
In multi-CID configurations, you can create an OAuth2 API Client Id/Secret in the "parent" CID that has access to the "child" or "member" CIDs. Some data is visible at the parent level, but some data is only visible within the child. After creating an API Client, you can use that to retrieve a list of all available member CIDs (or provide specific members using `-MemberCids`) and run PSFalcon commands within each child, while pausing between authorization token request attempts to avoid rate limiting.
```powershell
#Requires -Version 5.1
using module @{ ModuleName = 'PSFalcon'; ModuleVersion = '2.0' }
[CmdletBinding()]
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $ClientId,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{40}$')]
    [string] $ClientSecret,

    [Parameter()]
    [ValidateSet('eu-1', 'us-gov-1', 'us-1', 'us-2')]
    [string] $Cloud,

    [Parameter()]
    [ValidatePattern('^\w{32}$')]
    [array] $MemberCids
)
begin {
    $TokenParam = @{}
    @('ClientId', 'ClientSecret', 'Cloud').foreach{
        if ($PSBoundParameters.$_) {
            $TokenParam[$_] = $PSBoundParameters.$_
        }
    }
    if (!$MemberCids) {
        # Gather available Member CIDs
        Request-FalconToken @TokenParam
        if ((Test-FalconToken).Token -eq $true) {
            [array] $MemberCids = (Get-FalconMemberCid -Detailed -All | Where-Object {
                $_.status -eq 'active' }).child_cid
            Revoke-FalconToken
        }
    }
}
process {
    foreach ($Cid in $MemberCids) {
        try {
            Request-FalconToken @TokenParam -MemberCid $Cid
            if ((Test-FalconToken).Token -eq $true) {
                # Insert code to run and output data from each CID here
            }
        } catch {
            Write-Error $_
        } finally {
            if ((Test-FalconToken).Token -eq $true) {
                Revoke-FalconToken
            }
            Start-Sleep -Seconds 5
        }
    }
}
```
# Ingesting data
## Retrieve items from a text file or CSV
Collect a list of items (identifiers, hostnames, group names, etc.) from a text file, exclude blank values and save to the variable `$Items`, which can be used with a PSFalcon command.
```powershell
#Requires -Version 5.1
param(
    [Parameter(Mandatory = $true)]
    [ValidateScript({
        if (Test-Path $_) {
            $true
        } else {
            throw "Cannot find path '$_' because it does not exist."
        }
    })]
    [string] $Path
)
$InputFile = if (![IO.Path]::IsPathRooted($PSBoundParameters.Path)) {
    $FullPath = Join-Path -Path (Get-Location).Path -ChildPath $PSBoundParameters.Path
    $FullPath = Join-Path -Path $FullPath -ChildPath '.'
    [IO.Path]::GetFullPath($FullPath)
} else {
    $PSBoundParameters.Path
}
$Items = ((Get-Content -Path $InputFile).Normalize()).foreach{
    if (![string]::IsNullOrEmpty($_)) { $_ }
}
```
Collecting a list of hostnames (using the column `Hostname`) from a CSV can be done by modifying the `$Items` line.
```powershell
$Items = ((Import-Csv -Path $InputFile).Hostname).foreach{
    if (![string]::IsNullOrEmpty($_)) { $_ }
}
```
## Retrieve identifiers using a list
The `Filter` parameter \(a Falcon Query Language statement\) will accept 20 conditions at a time. If you have a list of hostnames that you need to match with their identifiers, you can loop through the list and output the hostname and identifier as new objects in an array contained in `$Hosts`. The example below assumes you have already ingested the list of hostnames into the `$Items` variable.
```powershell
#Requires -Version 5.1
using module @{ ModuleName = 'PSFalcon'; ModuleVersion = '2.0' }
$Hosts = for ($i = 0; $i -lt $Items.count; $i += 20) {
    # Retrieve device_id for hostnames in groups of 20
    $Filter = ($Items[$i..($i + 19)] | ForEach-Object {
        if (![string]::IsNullOrEmpty($_)) { "hostname:['$_']" }
    }) -join ','
    Get-FalconHost -Filter $Filter -Detailed | Select-Object hostname, device_id
}
```
# Manipulating Objects
## Add properties to an object
Most PSFalcon commands return `[PSCustomObject]` results. One of the [fastest ways](https://ramblingcookiemonster.github.io/Decorating-Objects/) to add properties to a `[PSCustomObject]` can be converted into a simple function that you can re-use.
```powershell
#Requires -Version 5.1
function Add-Property ($Object, $Name, $Value) {
    # Add property to [PSCustomObject]
    $Object.PSObject.Properties.Add((New-Object PSNoteProperty($Name, $Value)))
}
```
For example, if you wanted to add property `test` with value `abc` to a `Get-FalconHost` result:
```powershell
$HostObject = Get-FalconHost -Filter "hostname:'EXAMPLE-PC'" -Detailed
Add-Property -Object $HostObject -Name 'test' -Value 'abc'
```
## Iterate properties of an object
Different types of objects require different methods to figure out what properties are available in an object. Most PSFalcon command results are arrays of `[PSCustomObject]` values, which allows manipulation in several different ways, but they're not always easy to understand to someone inexperienced with PowerShell.

It's easiest to start with your result saved to a variable:
```powershell
PS>$Hosts = Get-FalconHost -Detailed
```
From there, you can use `Select-Object` to choose certain properties:
```powershell
PS>$Hosts | Select-Object device_id, hostname, local_ip

device_id   hostname     local_ip
---------   --------     --------
<redacted>  EXAMPLE-PC1  192.168.0.10
<redacted>  EXAMPLE-PC2  192.168.0.11

```
`Where-Object` can be used to filter for results with specific properties, using an exact match, or a RegEx match:
```powershell
PS>$Hosts | Where-Object { $_.hostname -eq 'EXAMPLE-PC2' } | Select-Object device_id, hostname, local_ip

device_id   hostname     local_ip
---------   --------     --------
<redacted>  EXAMPLE-PC2  192.168.0.11

PS>$Hosts | Where-Object { $_.hostname -match 'PC2' } | Select-Object device_id, hostname, local_ip

device_id   hostname     local_ip
---------   --------     --------
<redacted>  EXAMPLE-PC2  192.168.0.11
```
`Group-Object` can help determine counts, like devices by `agent_version`, or devices by `os_version`:
```powershell
PS>$Hosts | Group-Object agent_version

Count Name                      Group
----- ----                      -----
    2 6.26.14003.0              {@{device_id=...

PS>$Hosts | Group-Object os_version

Count Name                      Group
----- ----                      -----
    2 Windows 10                {@{device_id=...
```
Things become more complex when you don't know what properties are available, and it can be made more difficult when those properties aren't part of the object. For example, the Falcon APIs will omit properties when they aren't present, like when a device is not joined to a domain:
```powershell
PS>$Hosts | Select-Object device_id, hostname, machine_domain

device_id   hostname     machine_domain
---------   --------     --------
<redacted>  EXAMPLE-PC1  
<redacted>  EXAMPLE-PC2  example.com
```
To determine the number of properties that are present on both objects, it's easy to count the array itself. Unfortunately, PowerShell will only display the properties of the first object in the array. Properties for each object are only displayed when checking each object individually:
```powershell
PS>($Hosts | Get-Member | Where-Object { $_.MemberType -eq 'NoteProperty' }).Count
42
PS>$Hosts | ForEach-Object { ($_ | Get-Member | Where-Object { $_.MemberType -eq 'NoteProperty' }).Count }
42
45
```
Checking each object for the property names, then grouping them and selecting the unique properties can provide a list of the available property names across all objects in the array:
```powershell
PS>($Hosts | ForEach-Object { ($_ | Get-Member | Where-Object { $_.MemberType -eq 'NoteProperty' }).Name } | Group-Object).Name
agent_load_flags
agent_local_time
agent_version
...
```
***
The examples provided above are for example purposes only and are offered 'as is' with no support.
***