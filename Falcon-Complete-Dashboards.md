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
VERBOSE: [Read-Meta] pagination_total: <int_value>
```
```powershell
Get-FalconCompleteCollection -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/devicecount-collections/v1
VERBOSE: [Read-Meta] pagination_total: <int_value>
```
```powershell
Get-FalconCompleteIncident -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/incidents/v1
VERBOSE: [Read-Meta] pagination_total: <int_value>
```
## Getting identifiers or totals for allowlists, blocklists, escalations, and remediations
### Search for Falcon Complete allowlist, blocklist, escalation, or remediation identifiers
```powershell
Get-FalconCompleteAllowlist [-All]
```
```powershell
Get-FalconCompleteBlocklist [-All]
```
```powershell
Get-FalconCompleteEscalation [-All]
```
```powershell
Get-FalconCompleteRemediation [-All]
```
### Display the total number of Falcon Complete allowlist, blocklist, escalation, and remediation tickets
**NOTE**: The total value is returned in the response header and displayed in the Verbose stream by PSFalcon as `pagination_total`. It is not output as part of the typical response but is exposed when using the `-Verbose` parameter.
```powershell
Get-FalconCompleteAllowlist -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/allowlist/v1
VERBOSE: [Read-Meta] pagination_total: <int_value>
```
```powershell
Get-FalconCompleteBlocklist -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/blocklist/v1
VERBOSE: [Read-Meta] pagination_total: <int_value>
```
```powershell
Get-FalconCompleteEscalation -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/escalations/v1
VERBOSE: [Read-Meta] pagination_total: <int_value>
```
```powershell
Get-FalconCompleteRemediation -Verbose
VERBOSE: [Invoke-Endpoint] GET .../falcon-complete-dashboards/queries/remediations/v1
VERBOSE: [Read-Meta] pagination_total: <int_value>
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/151/falcon-complete-dashboard-apis)._