***
The examples provided below are for example purposes only and are offered 'as is' with no support.
***
### Authentication
* [Request authorization token and run commands](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples#request-authorization-token-and-run-commands)
* [Authorize and run commands in member CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples#authorize-and-run-commands-in-member-cids)
### Ingesting Data
* [Retrieve items from a text file or CSV](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples#retrieve-items-from-a-text-file-or-csv)
### Manipulating Objects
* [Add properties to an object](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples#add-properties-to-an-object)
***
# Authentication
## Request authorization token and run commands
An example of how to include OAuth2 API Client information as parameters and perform an authorization token request to the associated CID or "member" CID.
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
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
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
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
            Request-FalconToken @TokenParam
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
    if ($_ -ne '') {
        $_
    }
}
```
Collect a list of hostnames from a CSV, using the column 'Hostname':
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
$Items = (Import-Csv -Path $InputFile).Hostname
```
# Manipulating Objects
### Add properties to an object
Most PSFalcon commands return `[PSCustomObject]` results. One of the [fastest ways](https://ramblingcookiemonster.github.io/Decorating-Objects/) to add properties to a `[PSCustomObject]` can be converted into a simple function that you can re-use.
```powershell
#Requires -Version 5.1
function Add-Field ($Object, $Name, $Value) {
    # Add property to [PSCustomObject]
    $Object.PSObject.Properties.Add((New-Object PSNoteProperty($Name, $Value)))
}
```
For example, if you wanted to add property `test` with value `abc` to a `Get-FalconHost` result:
```powershell
$HostObject = Get-FalconHost -Filter "hostname:'EXAMPLE-PC'" -Detailed
Add-Field -Object $HostObject -Name 'test' -Value 'abc'
```
***
The examples provided above are for example purposes only and are offered 'as is' with no support.
***