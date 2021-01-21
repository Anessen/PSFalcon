## Find incidents
```powershell
Get-FalconIncident [-Detailed] [-All]
```
### Find behaviors
```powershell
Get-FalconBehavior [-Detailed] [-All]
```
### Update the status of multiple incidents
```powershell
Invoke-FalconIncidentAction -Name update_status -Value in_progress -Ids <id>, <id>
```
**NOTE**: Corresponding detections can be updated with the `-UpdateDetects` and `-OverwriteDetects` parameters, using a value of `$true`.
## Find detections
```powershell
Get-FalconDetection -Filter "status:'new'+first_behavior:>'2020-01-01'" -Sort first_behavior.desc [-Detailed] [-All]
```
### Modify the status of multiple detections
**NOTE**: `Edit-FalconDetection` will automatically group requests in batches of 1,000 detections.
```powershell
Edit-FalconDetection -Ids <id>, <id> -Status new
```
### Hide detections from the UI
**WARNING**: Hiding detections is not reversible!
```powershell
Edit-FalconDetection -Ids <id>, <id> -ShowInUi $false
```
## Show CrowdScores
```powershell
Get-FalconScore [-All]
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/86/detections-monitoring-apis)._