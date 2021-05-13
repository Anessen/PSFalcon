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
Get-FalconCompleteDetection -Total
<int_value>
```
```powershell
Get-FalconCompleteCollection -Total
<int_value>
```
```powershell
Get-FalconCompleteIncident -Total
<int_value>
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
Get-FalconCompleteAllowlist -Total
<int_value>
```
```powershell
Get-FalconCompleteBlocklist -Total
<int_value>
```
```powershell
Get-FalconCompleteEscalation -Total
<int_value>
```
```powershell
Get-FalconCompleteRemediation -Total
<int_value>
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/151/falcon-complete-dashboard-apis)._