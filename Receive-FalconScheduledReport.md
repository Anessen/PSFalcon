# Receive-FalconScheduledReport
## SYNOPSIS
Download a scheduled report or search result
## DESCRIPTION
Requires 'Scheduled Reports: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|Object|Destination path|||||X|
|Id|String|Report identifier||||X|X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconScheduledReport [[-Path] <Object>] [-Id] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /reports/entities/report-executions-download/v1
```
### falconpy
[report_executions_download_get](https://github.com/CrowdStrike/falconpy/wiki/report-executions#report_executions_download_get)
## USAGE
### Download a report file by execution ID
```powershell
Receive-FalconScheduledReport -Id <id> -Path <string>
```
_See [Download your most recent scheduled report results](https://github.com/CrowdStrike/psfalcon/blob/master/samples/scheduled_reports/download-your-most-recent-scheduled-report-results.ps1)._

_2023-04-25: PSFalcon v2.2.5_
