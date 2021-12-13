![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
![Twitter URL](https://img.shields.io/twitter/url?label=Follow%20%40CrowdStrike&style=social&url=https%3A%2F%2Ftwitter.com%2FCrowdStrike)
# Requesting a token
During a PowerShell session, you must have a valid OAuth2 access token in order to make requests to the CrowdStrike Falcon APIs.

If you have already provided your credentials, PSFalcon requests a token on your behalf when you issue a command. Otherwise, you must request a token and provide the credentials. You can do this using `Request-FalconToken`, or input your ClientId/ClientSecret when prompted after issuing a PSFalcon command.

**NOTE**: If you allow the module to prompt for your ClientId/ClientSecret, you will default to the 'us-1' Cloud.
```powershell
Request-FalconToken
ClientId: <string>
ClientSecret: <string>
```
After a valid OAuth2 token is received, it is cached with your credentials. Your cached token is checked and refreshed as needed while running PSFalcon commands.

## Child environments
If you're using an MSSP ("Flight Control") configuration, you can target specific child environments using the `-MemberCid` parameter during authentication token requests. Your choice is saved and all requests are sent to that particular member CID unless a new `Request-FalconToken` request is made specifying a new member CID.

## Alternate clouds
Authentication token requests are sent to the `us-1` cloud by default. You may use the `-Cloud` parameter to choose a different Cloud environment, or `-Hostname` to set it using the full URL value.

The accepted hostname values can be viewed using tab auto-completion after entering the `-Cloud` or `-Hostname` parameter(s). Your Cloud/Hostname choice is saved and all requests are sent using the cached information.

# Revoking a token
Authentication tokens expire after 30 minutes. If you wish to revoke an existing token, you can use `Revoke-FalconToken`.

**NOTE**: Revoking a token will also clear your credentials. This is useful if you wish to switch between different Falcon environments.
```powershell
Revoke-FalconToken
```
# Verifying token status
`Test-FalconToken` can be used to verify whether you have an active OAuth2 access token cached. The `Token` property of the output from `Test-FalconToken` provides a `[boolean]` value of your current status.
```powershell
(Test-FalconToken).Token
```
# Credential handling
PSFalcon does not provide a method for securely handling your API client credentials. To encrypt your API client information, you'll need a third-party solution. The [Microsoft.PowerShell.SecretStore](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.secretstore/?view=ps-modules) module is a cross-platform option that works with PSFalcon. You can follow the steps below to install the module and use it with `Request-FalconToken`.

*NOTE*: [Microsoft.PowerShell.SecretManagement](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.secretmanagement/?view=ps-modules) is a pre-requisite for the Microsoft.PowerShell.SecretStore module. It will be installed during the `Install-Module` step.
```
Install-Module -Name Microsoft.PowerShell.SecretStore -Scope CurrentUser
```

*NOTE*: Using the default configuration, Microsoft.PowerShell.SecretStore will prompt for a password to access your secret vault. You can remove the password requirement to use the vault with a script or as part of a scheduled task, which leaves the vault accessible to the account that was used to create it. You will be asked to create, confirm and remove a password after entering this command.
```
Set-SecretStoreConfiguration -Scope CurrentUser -Authentication None -Interaction None
```

Once the module is installed and configured as desired, create a vault to store your API client(s):
```
Register-SecretVault -ModuleName Microsoft.PowerShell.SecretStore -Name MyVault
```

`Request-FalconToken` requires multiple parameters to request a token. Each individual API client can be stored with the relevant parameters in your new vault:
```
$ApiClient = @{
    ClientId     = 'my_client_id'
    ClientSecret = 'my_client_value'
    Hostname     = 'https://api.crowdstrike.com'
}
Set-Secret -Name MyApiClient -Secret $ApiClient -Vault MyVault
```

Once stored, they can be retrieved using your chosen `-Name`, and you can [splat](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.2) the parameters with `Request-FalconToken`:
```
Get-Secret -Name MyApiClient -Vault MyVault -AsPlainText | ForEach-Object { Request-FalconToken @_ }
```

If desired, a simple function can be added to your [PowerShell profile](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.2) to retrieve your credentials and request a token by name:
```
function Request-SecretToken ([string] $Name) {
    if (-not(Get-Module -Name PSFalcon)) {
        Import-Module -Name PSFalcon
    }
    if ((Test-FalconToken -ErrorAction SilentlyContinue).Token -eq $true) {
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
```
Request-SecretToken MyApiClient
```
_Learn more about [Commands](https://github.com/CrowdStrike/psfalcon/wiki/Commands)._