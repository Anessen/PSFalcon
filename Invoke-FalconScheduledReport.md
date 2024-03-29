# Invoke-FalconScheduledReport
## SYNOPSIS
Execute a scheduled report
## DESCRIPTION
Requires 'Scheduled Reports: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Report identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconScheduledReport [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /reports/entities/scheduled-reports/execution/v1
```
### falconpy
[scheduled_reports_launch](https://github.com/CrowdStrike/falconpy/wiki/scheduled-reports#scheduled_reports_launch)
## USAGE
## Execute a scheduled report on demand
```powershell
Invoke-FalconScheduledReport -Id <id>
```
_See [Get-FalconScheduledReport](Get-FalconScheduledReport)._

_2023-04-25: PSFalcon v2.2.5_
