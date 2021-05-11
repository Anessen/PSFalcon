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
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/162/falcon-x-recon-apis)._