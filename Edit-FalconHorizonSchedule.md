# Edit-FalconHorizonSchedule
## SYNOPSIS
Modify Falcon Horizon scan schedules
## DESCRIPTION
Requires 'CSPM registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ScanSchedule|String|Scan interval|||`2h`<BR>`6h`<BR>`12h`<BR>`24h`||X|
|CloudPlatform|String|Cloud platform|||`aws`<BR>`azure`<BR>`gcp`||X|
|NextScanTimestamp|String|Next scan timestamp (RFC3339)|||||X|
## SYNTAX
```powershell
Edit-FalconHorizonSchedule [-ScanSchedule] <String> [-CloudPlatform] <String> [[-NextScanTimestamp] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /settings/scan-schedule/v1
```
### falconpy
[UpdateCSPMScanSchedule](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#UpdateCSPMScanSchedule)
## USAGE
### Updating the assessment schedule
```powershell
Edit-FalconHorizonSchedule -CloudPlatform aws -ScanSchedule 2h
```

_2023-04-25: PSFalcon v2.2.5_
