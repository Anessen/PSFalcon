## Listing commands
After importing the module you can view the list of commands provided with PSFalcon:

```powershell
Get-Command -Module PSFalcon
```

## Getting Help (v2.0.8)
Because PSFalcon uses dynamic parameters, the traditional PowerShell `Get-Help` command doesn't show parameters that can be used with PSFalcon commands. Instead, use `<command> -Help` to call a custom function that displays information about the available parameters and a basic description of their use.

```powershell
PS> Request-FalconToken -Help

## Request an OAuth2 access token

  -ClientId [String]
    OAuth2 API client identifier
      Position : 1
      Pattern : \w{32}

  -ClientSecret [String]
    OAuth2 API client secret
      Position : 2
      Pattern : \w{40}

  -Cloud [String]
    Destination cloud
    Enum : eu-1, us-gov-1, us-1, us-2  
    Position : 3

  -MemberCid [String]
    Child environment to use for authentication in multi-CID configurations
      Position : 4
      Pattern : \w{32}
```
## Getting Help (v2.1.0+)
Information about PSFalcon commands and their parameters is available using the PowerShell `Get-Help` command. Using the `-Examples`, `-Detailed` or `-Full` parameter(s) provides additional information.
```powershell
Get-Help Request-FalconToken
```
_Learn more about [Parameters](https://github.com/CrowdStrike/psfalcon/wiki/Parameters) and [Filtering](https://github.com/CrowdStrike/psfalcon/wiki/Filtering-and-the-Falcon-Query-Language)._