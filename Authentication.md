![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)

# Authentication
![API Documentation](https://img.shields.io/badge/API%20Documentation-maroon?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAOCAYAAAAi2ky3AAABhWlDQ1BJQ0MgcHJvZmlsZQAAKJF9kT1Iw1AUhU9TpaIVBzuIOGSoDmJBVEQ3rUIRKoRaoVUHk5f+CE0akhQXR8G14ODPYtXBxVlXB1dBEPwBcXNzUnSREu9LCi1ifPB4H+e9c7jvXkColZhmtY0Cmm6bqURczGRXxNAruhAEMI1hmVnGrCQl4bu+7hHg512MZ/m/+3N1qzmLAQGReIYZpk28Tjy5aRuc94kjrCirxOfEIyYVSPzIdcXjN84FlwWeGTHTqTniCLFYaGGlhVnR1IgniKOqplO+kPFY5bzFWStVWKNO/sNwTl9e4jrtASSwgEVIEKGggg2UYCNGp06KhRTdx338/a5fIpdCrg0wcsyjDA2y6wefwe/eWvnxMS8pHAfaXxznYxAI7QL1quN8HztO/QQIPgNXetNfrgFTn6RXm1r0COjZBi6um5qyB1zuAH1PhmzKrsTnL+TzwPsZjSkL9N4Cnate3xr3OH0A0tSr5A1wcAgMFSh7zeffHa19+/dNo38/hq9yr+iELI0AAAAGYktHRAAAAAAAAPlDu38AAAAJcEhZcwAACxMAAAsTAQCanBgAAAAHdElNRQflDAsTByz7Va2cAAAAGXRFWHRDb21tZW50AENyZWF0ZWQgd2l0aCBHSU1QV4EOFwAAAYBJREFUKM+lkjFIlVEYht/zn3sFkYYUyUnIRcemhCtCU6JQOLiIU+QeJEQg6BBIm0s4RBCBLjq5OEvgJC1uOniJhivesLx17/97/vO9b4NK4g25157hfHCGB773/cA0HZIEAKiMj+LWiOxljG/i96pnCFP58XHnrWX2+9cj0dYl9Yu2FE9/9rXrcAAgs2eSyiBfOe/XRD503h/CuffOubQVUXL+Jh9BllzBbyJJBgDclVkO4Kukd8zzkXJbeUljIldFTstsmSHM6S81ma2KfPKlFdkGAMY4wzx/bbXapMy21My+YizdKNq5mDzLkrxafSxySFKjSWX2oTmjKzz4vN0r2lOFcL/Q3V0/mX95ILMXTTGYVfaut/aP2+oCMAvnZgCcsF5fcR0dg65YHAdwB+QApADvu0AuOe/ftlJAD7Nsgmm6yBjDtfWORJZlNtFyo/lR5Z7MyheKA5ktSur7sTAHazSG27pehjAiaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)[![EU 1](https://img.shields.io/badge/-EU--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.eu-1.crowdstrike.com/support/documentation/93/oauth2-auth-token-apis)[![US-1](https://img.shields.io/badge/-US--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.crowdstrike.com/support/documentation/93/oauth2-auth-token-apis)[![US-2](https://img.shields.io/badge/-US--2-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.us-2.crowdstrike.com/support/documentation/93/oauth2-auth-token-apis)[![US-GOV-1](https://img.shields.io/badge/-US--GOV--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.laggar.gcw.crowdstrike.com/support/documentation/93/oauth2-auth-token-apis)
- [Get an auth token](#get-an-auth-token)
    - [Alternate clouds](#alternate-clouds)
    - [Child environments](#child-environments)
- [Verifying token status](#verifying-token-status)
- [Revoke an auth token](#revoke-an-auth-token)
- [Securing credentials](#securing-credentials)
- [Authentication within a script](#authentication-within-a-script)
    - [Request authorization token and run a command](#request-authorization-token-and-run-a-command)
    - [Authorize and run commands across member CIDs](#authorize-and-run-commands-across-member-CIDs)
***
|Command|Permission|
|-------|----------|
|[Request-FalconToken](#get-an-auth-token)||
|[Revoke-FalconToken](#revoke-an-auth-token)||
|[Test-FalconToken](#verifying-token-status)||
***
## Get an auth token
During a PowerShell session, you must have a valid OAuth2 access token in order to make requests to the CrowdStrike
Falcon APIs. You can do this using `Request-FalconToken`, or input your ClientId/ClientSecret when prompted after
issuing a PSFalcon command.

After a valid OAuth2 token is received, it is cached with your credentials. Your cached token is checked and
refreshed as needed while running PSFalcon commands.
```powershell
Request-FalconToken -ClientId 'client_id' -ClientSecret 'client_secret'
```
**WARNING**: `Request-FalconToken` defaults to the `us-1` cloud. If your environment exists within a different
cloud, the module will attempt to use automatic redirection, except when the target cloud is `us-gov-1`. Defining
`-Cloud` or `-Hostname` ensures that your token request goes to the proper cloud without relying on re-direction
and is required when using `us-gov-1`.
### Alternate clouds
Authentication token requests are sent to the `us-1` cloud by default. You may use the `-Cloud` or `-Hostname`
parameters to set it using a cloud, or full URL value. The accepted hostname values can be viewed using tab
auto-completion. Your Cloud/Hostname choice is saved and all requests are sent using the cached information.
### Child environments
In MSSP (also known as "Flight Control") configurations, you can target specific child environments ("CIDs")
using the `-MemberCid` parameter during authentication token requests. Your choice is saved and all requests are
sent to that particular member CID unless a new `Request-FalconToken` request is made specifying a new member CID,
or you `Revoke-FalconToken`.
## Verifying token status
`Test-FalconToken` can be used to verify whether you have an active OAuth2 access token cached.
```powershell
Test-FalconToken

Token Hostname                    ClientId                         MemberCid
----- --------                    --------                         ---------
 True https://api.crowdstrike.com <redacted>

```
The `Token` property of the output from `Test-FalconToken` provides a `[boolean]` value of your current status.
```powershell
(Test-FalconToken).Token
True
```
## Revoke an auth token
The command `Revoke-FalconToken` will revoke your current authorization token and clear it from your local cache.
```powershell
Revoke-FalconToken
```
## Securing credentials
PSFalcon does not provide a method for securely handling your API client credentials. The [Microsoft.PowerShell.SecretStore](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.secretstore/?view=ps-modules) module is a
cross-platform option that works with PSFalcon. You can follow the steps below to install the module and use it
with `Request-FalconToken`.

*NOTE*: [Microsoft.PowerShell.SecretManagement](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.secretmanagement/?view=ps-modules) is a pre-requisite for the `Microsoft.PowerShell.SecretStore`
module. It will be installed during the `Install-Module` step.
```powershell
Install-Module -Name Microsoft.PowerShell.SecretStore -Scope CurrentUser
```
*NOTE*: Using the default configuration, `Microsoft.PowerShell.SecretStore` will prompt for a password to access
your secret vault. You can remove the password requirement to use the vault with a script or as part of a
scheduled task, which leaves the vault accessible to the account that was used to create it. You will be asked to
create, confirm and remove a password after entering this command.
```powershell
Set-SecretStoreConfiguration -Scope CurrentUser -Authentication None -Interaction None
```
Once the module is installed and configured as desired, create a vault to store your API client(s):
```powershell
Register-SecretVault -ModuleName Microsoft.PowerShell.SecretStore -Name MyVault
```
`Request-FalconToken` requires multiple parameters to request a token. Each individual API client can be stored
with the relevant parameters (including `MemberCid`) in your new vault:
```powershell
$ApiClient = @{
    ClientId     = 'my_client_id'
    ClientSecret = 'my_client_value'
    Hostname     = 'https://api.crowdstrike.com'
}
Set-Secret -Name MyApiClient -Secret $ApiClient -Vault MyVault
```
Once stored, credentials can be retrieved using your chosen `-Name`, and you can [splat the parameters](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_splatting) with
`Request-FalconToken`:
```powershell
Get-Secret -Name MyApiClient -Vault MyVault -AsPlainText | ForEach-Object { Request-FalconToken @_ }
```

If desired, a simple function can be added to [your PowerShell profile](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles) to retrieve your credentials and request a
token by name:
```powershell
function Request-SecretToken ([string] $Name) {
    if (-not(Get-Module -Name PSFalcon)) {
        Import-Module -Name PSFalcon
    } elseif ((Test-FalconToken -ErrorAction SilentlyContinue).Token -eq $true) {
        Revoke-FalconToken
    }
    $Secret = Get-Secret -Name $Name -Vault MyVault -AsPlainText
    if ($Secret) {
        Request-FalconToken @Secret
    } else {
        throw "No secret found matching '$String'."
    }
}
```
Once added to your profile, you can retrieve your credential set and request a token in a single step:
```powershell
Request-SecretToken MyApiClient
```
## Authentication within a script
### Request authorization token and run a command
The request of an authorization token can happen as part of a script that performs other tasks. Here is a re-usable
example which defines the necessary parameters, and can optionally authenticate within a specific member CID (found
within Flight Control environments).
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$ClientId,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^\w{40}$')]
    [string]$ClientSecret,
    [Parameter(Position=3)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$MemberCid,
    [Parameter(Position=4)]
    [ValidateSet('us-1','us-2','us-gov-1','eu-1')]
    [string]$Cloud
)
begin {
    $Token = @{}
    @('ClientId','ClientSecret','Cloud','MemberCid').foreach{
        if ($PSBoundParameters.$_) { $Token[$_] = $PSBoundParameters.$_ }
    }
}
process {
    try {
        Request-FalconToken @Token
        if ((Test-FalconToken).Token -eq $true) {
            # Insert code to run here
        }
    } catch {
        throw $_
    } finally {
        if ((Test-FalconToken).Token -eq $true) { Revoke-FalconToken }
    }
}
```
### Authorize and run commands across member CIDs
In multi-CID configurations, you can create an OAuth2 API Client Id/Secret in the "parent" CID that has access to
the "member" (a.k.a. "child") CIDs. A lot of data is visible at the parent level, but some data is only visible
within each child. After creating an API Client, you can use that to retrieve a list of all available member CIDs
(or provide specific members using `MemberCid`) and run PSFalcon commands within each child, while pausing between
authorization token request attempts to avoid rate limiting.
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$ClientId,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^\w{40}$')]
    [string]$ClientSecret,
    [Parameter(Position=3)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$MemberCid,
    [Parameter(Position=4)]
    [ValidateSet('us-1','us-2','us-gov-1','eu-1')]
    [string]$Cloud
)
begin {
    $Token = @{}
    @('ClientId','ClientSecret','Cloud').foreach{
        if ($PSBoundParameters.$_) { $Token[$_] = $PSBoundParameters.$_ }
    }
    if (!$MemberCid) {
        Request-FalconToken @Token
        if ((Test-FalconToken).Token -eq $true) {
            # Gather available Member CIDs
            [string[]]$MemberCid = Get-FalconMemberCid -Detailed -All | Where-Object { $_.status -eq 'active' } |
                Select-Object -ExpandProperty child_cid
            Revoke-FalconToken
        }
    }
}
process {
    foreach ($Cid in $MemberCid) {
        try {
            Request-FalconToken @Token -MemberCid $Cid
            if ((Test-FalconToken).Token -eq $true) {
                # Insert code to run in each CID here
            }
        } catch {
            Write-Error $_
        } finally {
            if ((Test-FalconToken).Token -eq $true) {
                Revoke-FalconToken
                Start-Sleep -Seconds 5
            }
        }
    }
}
```