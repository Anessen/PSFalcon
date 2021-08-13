# List available commands
After importing the module you can view the list of commands provided with PSFalcon:
```powershell
Get-Command -Module PSFalcon
```
# Using commands
## PSFalcon v2.1+
Information about PSFalcon commands and their parameters is available using the PowerShell `Get-Help` command. Using the `-Examples`, `-Detailed` or `-Full` parameter(s) provides additional information.
```powershell
Get-Help Request-FalconToken
```
## PSFalcon v2.0
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
## Users and Roles
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/87/users-and-roles-apis)._
### Create a new user
```powershell
New-FalconUser -Username jane.doe@example.com
```
### List all users
```powershell
Get-FalconUser [-Detailed]
```
### Get details on one or more users
```powershell
Get-FalconUser -Ids <id>, <id>
```
### Modify a user
```powershell
Edit-FalconUser -Id <id> -FirstName Jane -LastName Doe
```
### Remove a user
```powershell
Remove-FalconUser -Id <id>
```
### List all available user roles
```powershell
Get-FalconRole [-Detailed]
```
### List roles assigned to a user
```powershell
Get-FalconRole -UserId <id> [-Detailed]
```
### Assign roles to a user
```powershell
Add-FalconRole -Ids <id>, <id> -UserId <id>
```
### Revoke roles from a user
```powershell
Remove-FalconRole -Ids <id>, <id> -UserId <id>
```
## Zero Trust Assessment
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/156/zero-trust-assessment-apis)._
### Retrieving Zero Trust Assessment data by host
```powershell
Get-FalconZTA -Ids <id>, <id>
```