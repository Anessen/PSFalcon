## Managing monitoring rules
### Finding a monitoring rule
```powershell
Get-FalconReconRule [-Detailed]
```
### Creating a monitoring rule
```powershell
New-FalconReconRule -Name psfalcon_example -Topic SA_AUTHOR -Filter "author:'example_author'" -Priority low -Permissions private
```
### Creating multiple monitoring rules in a single request
```powershell
$Array = @(
    @{
        name = "psfalcon_example_1"
        topic = "SA_BRAND_PRODUCT"
        filter = "phrase:'psfalcon_example_phrase'"
        priority = "low"
        permissions = "private"
    },
    @{
        name = "psfalcon_example_2"
        topic = "SA_BIN"
        filter = "ccbin:'1234'"
        priority = "medium"
        permissions = "public"
    }
)
New-FalconReconRule -Array $Array
```
### Updating a monitoring rule
```powershell
Edit-FalconReconRule -Id <id> -Name psfalcon_example_updated -Priority medium
```
### Updating multiple monitoring rules in a single request
```powershell
$Array = @(
    @{
        id = <id>
        priority = "high"
    },
    @{
        id = <id>
        priority = "high"
    }
)
Edit-FalconReconRule -Array $Array
```
### Deleting a monitoring rule
```powershell
Remove-FalconReconRule -Ids <id>, <id>
```
## Setting up email notifications for monitoring rules
### Querying monitoring rule actions
```powershell
Get-FalconReconAction [-Detailed]
```
### Creating email notifications for a monitoring rule
```powershell
New-FalconReconAction -RuleId <rule_id> -Type email -Frequency daily -Recipients user@example.com
```
### Updating email notifications for a monitoring rule
```powershell
Edit-FalconReconAction -Id <id> -Frequency weekly
```
### Deleting email notifications for a monitoring rule
```powershell
Remove-FalconReconAction -Id <id>
```
## Managing notifications from monitoring rule matches
### Querying notifications
```powershell
```
## Getting data from notifications
### Get simplified data from notifications
```powershell
```
### Get raw intelligence data from notifications
```powershell
```
### Get data from notifications translated into English
```powershell
```
### Get raw intelligence data from notifications translated into English
```powershell
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/162/falcon-x-recon-apis)._