![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
## Installation, Upgrade and Removal
* Downloading and installing the module using the [PowerShell Gallery](https://github.com/CrowdStrike/psfalcon/wiki/Installation,-Upgrade-and-Removal#use-the-powershell-gallery) or [GitHub](https://github.com/CrowdStrike/psfalcon/wiki/Installation,-Upgrade-and-Removal#download-from-github)
* [Upgrading the module](https://github.com/CrowdStrike/psfalcon/wiki/Installation,-Upgrade-and-Removal#upgrade)
* [Removing the module](https://github.com/CrowdStrike/psfalcon/wiki/Installation,-Upgrade-and-Removal#removal)
## Importing, Syntax and Output
* [Importing into PowerShell](https://github.com/CrowdStrike/psfalcon/wiki/Importing,-Syntax-and-Output#Import-the-Module)
* [Finding commands](https://github.com/CrowdStrike/psfalcon/wiki/Importing,-Syntax-and-Output#List-available-commands)
* [Using parameters](https://github.com/CrowdStrike/psfalcon/wiki/Importing,-Syntax-and-Output#Using-parameters) and dealing with [pagination handling](https://github.com/CrowdStrike/psfalcon/wiki/Importing,-Syntax-and-Output#-all)
* [Converting output](https://github.com/CrowdStrike/psfalcon/wiki/Importing,-Syntax-and-Output#converting-output)
## Authentication
* [Requesting](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#get-an-auth-token) and [revoking](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#revoke-an-auth-token) OAuth2 access tokens, switching [cloud environments](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#alternate-clouds) and [child CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#child-environments)
* [Verifying access token status](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#verifying-token-status)
* [Securing credentials](https://github.com/CrowdStrike/psfalcon/wiki/Authentication#verifying-token-status)
## Filtering Results
* [Limiting results](https://github.com/CrowdStrike/psfalcon/wiki/Filtering-Results#Falcon-Query-Language) and [combining multiple filter conditions and values](https://github.com/CrowdStrike/psfalcon/wiki/Filtering-Results#multiple-values)
## Additional Examples
Individual commands and their required permissions are listed in the "Commands and Permissions" section, aligning with how they are displayed in the CrowdStrike Falcon API documentation. A few additional pages are included that cover PSFalcon-specific examples.
* [Export](https://github.com/CrowdStrike/psfalcon/wiki/Configuration-Export-and-Import#export-all-configurations) configured items, then [restore or re-create](https://github.com/CrowdStrike/psfalcon/wiki/Configuration-Export-and-Import#import-configurations) them
* [Example code](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples) to help with building scripts using PowerShell and PSFalcon
* [Basic scripts](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts) designed to fulfill various goals using PSFalcon
* [Send PSFalcon objects and events to Humio](https://github.com/CrowdStrike/psfalcon/wiki/Humio-Ingestion)