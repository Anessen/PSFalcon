# Get-FalconHorizonSchedule
## SYNOPSIS
Retrieve detailed information about Falcon Horizon schedules
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|CloudPlatform|String[]|Cloud platform|||`aws`<BR>`azure`<BR>`gcp`|X|X|
## SYNTAX
```powershell
Get-FalconHorizonSchedule [-CloudPlatform] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /settings/scan-schedule/v1
```
### falconpy
[GetCSPMScanSchedule](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMScanSchedule)
## USAGE
### Retrieving the assessment schedule
```powershell
Get-FalconHorizonSchedule [-CloudPlatform]
```

_2023-04-25: PSFalcon v2.2.5_
