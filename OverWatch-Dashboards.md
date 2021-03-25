## Getting global OverWatch totals for detections, events, and incidents
### Getting the total number of Falcon OverWatch detections for the past 48 hours
```powershell
Get-FalconOverWatchDetection -Filter "detect_time:>'now-48h'"
```
### Getting the total number of Falcon OverWatch incidents for the past 48 hours
```powershell
Get-FalconOverWatchIncident -Filter "detect_time:>'now-48h'"
```
### Getting the total number of Falcon OverWatch events
```powershell
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/155/falcon-overwatch-dashboard-apis)._