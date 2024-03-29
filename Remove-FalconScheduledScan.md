# Remove-FalconScheduledScan
## SYNOPSIS
Remove a scheduled scan
## DESCRIPTION
Requires 'On-demand scans (ODS): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Scheduled scan identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to find scheduled scans for removal||||||
## SYNTAX
```powershell
Remove-FalconScheduledScan -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Remove-FalconScheduledScan -Filter <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /ods/entities/scheduled-scans/v1
```
### falconpy
[delete_scheduled_scans](https://github.com/CrowdStrike/falconpy/wiki/ods#delete_scheduled_scans)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
