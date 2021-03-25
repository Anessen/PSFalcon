## Getting identifiers or totals for detections, device count collections, and incidents
### Search for Falcon Complete detection, device collection or incident identifiers
```powershell
Get-FalconCompleteDetection [-All]
```
```powershell
Get-FalconCompleteCollection [-All]
```
```powershell
Get-FalconCompleteIncident [-All]
```
### Display the total number of Falcon Complete detections, device collections or incidents
**NOTE**: The total value is returned in the response header and displayed in the Verbose stream by PSFalcon as `pagination_total`. It is not output as part of the typical response but is exposed when using the `-Verbose` parameter.
```powershell
Get-FalconCompleteDetection -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/detects/v1
VERBOSE: [Read-Meta] pagination_total: <decimal_total_value>
```
```powershell
Get-FalconCompleteCollection -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/devicecount-collections/v1
VERBOSE: [Read-Meta] pagination_total: <decimal_total_value>
```
```powershell
Get-FalconCompleteIncident -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/incidents/v1
VERBOSE: [Read-Meta] pagination_total: <decimal_total_value>
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/151/falcon-complete-dashboard-apis)._