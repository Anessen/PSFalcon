***
The examples provided below are for example purposes only and are offered 'as is' with no support.
***
### Authentication
* [Request authorization token and run commands](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples#request-authorization-token-and-run-commands)
* [Authorize and run commands in member CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples#request-authorization-token-and-run-commands)
### Ingesting Data
* [Retrieve identifiers from a text file](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples#request-authorization-token-and-run-commands)
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
## Retrieve identifiers from a text file
To perform certain actions, you'll need an identifier for a specific resource within your Falcon environment--Host identifiers for Real-time Response or Network Containment, Host Group identifiers for policy assignment, etc.

The following example shows how you can add the retrieval of these identifiers, convert to an absolute file path, normalize the input (which sometimes is a problem when the values are converted to Json for an API request) and ignore any blank values. Once complete, you can use the `$Ids` variable with another PSFalcon command.
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
$Ids = ((Get-Content -Path $InputFile).Normalize()).foreach{
    if ($_ -ne '') {
        $_
    }
}
```
***
The examples provided above are for example purposes only and are offered 'as is' with no support.
***