![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
## Installation, Upgrade and Removal
* Downloading and installing the module using the [PowerShell Gallery](Installation,-Upgrade-and-Removal#use-the-powershell-gallery) or [GitHub](Installation,-Upgrade-and-Removal#download-from-github)
* [Upgrading the module](Installation,-Upgrade-and-Removal#upgrade)
* [Removing the module](Installation,-Upgrade-and-Removal#removal)
## Importing, Syntax and Output
* [Importing into PowerShell](Importing,-Syntax-and-Output#Import-the-Module)
* [Finding commands](Importing,-Syntax-and-Output#List-available-commands)
* [Using parameters](Importing,-Syntax-and-Output#Using-parameters) and dealing with [pagination handling](Importing,-Syntax-and-Output#all)
* [Converting output](Importing,-Syntax-and-Output#converting-output)
## Authentication
* [Requesting](Authentication#get-an-auth-token) and [revoking](Authentication#revoke-an-auth-token) OAuth2 access tokens, switching [cloud environments](Authentication#alternate-clouds) and [child CIDs](Authentication#child-environments)
* [Verifying access token status](Authentication#verifying-token-status)
* [Securing credentials](Authentication#securing-credentials)
## Filtering Results
* [Limiting results](Filtering-Results#Falcon-Query-Language) and [combining multiple filter conditions and values](Filtering-Results#multiple-values)
## Additional Examples
Individual commands and their required permissions are listed in their relevant section. A few additional pages are included that cover PSFalcon-specific examples.
* [Export](Export-FalconConfig) configured items, then [restore or re-create](Import-FalconConfig) them
* [Example code](Code-Examples) to help with building scripts using PowerShell and PSFalcon
* [Samples](https://github.com/CrowdStrike/psfalcon/tree/master/samples) designed to fulfill various goals using PSFalcon
* Send PSFalcon objects to [Humio or a webhook](Third-party-ingestion)