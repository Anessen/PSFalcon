# Get-FalconScheduledReport
## SYNOPSIS
Search for scheduled report or searches and their execution information
## DESCRIPTION
Requires 'Scheduled Reports: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Scheduled report or scheduled search identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`created_on`<BR>`description`<BR>`expiration_on`<BR>`last_execution.last_updated_on`<BR>`last_execution.status`<BR>`last_updated_on`<BR>`name`<BR>`next_execution_on`<BR>`shared_with`<BR>`start_on`<BR>`status`<BR>`stop_on`<BR>`type`<BR>`user_id`<BR><BR>Execution:<BR>`created_on`<BR>`expiration_on`<BR>`last_updated_on`<BR>`result_metadata`<BR>`scheduled_report_id`<BR>`shared_with`<BR>`status`<BR>`type`<BR>`user_id`||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`created_on.asc`<BR>`created_on.desc`<BR>`last_updated_on.asc`<BR>`last_updated_on.desc`<BR>`last_execution_on.asc`<BR>`last_execution_on.desc`<BR>`next_execution_on.asc`<BR>`next_execution_on.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Execution|Switch|Retrieve information about scheduled report execution||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconScheduledReport [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScheduledReport -Id <String[]> -Execution [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScheduledReport -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScheduledReport [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Execution [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /reports/entities/report-executions/v1
GET /reports/entities/scheduled-reports/v1
GET /reports/queries/report-executions/v1
GET /reports/queries/scheduled-reports/v1
```
### falconpy
[scheduled_reports_query](https://github.com/CrowdStrike/falconpy/wiki/scheduled-reports#scheduled_reports_query)<BR>[report_executions_get](https://github.com/CrowdStrike/falconpy/wiki/report-executions#report_executions_get)<BR>[scheduled_reports_get](https://github.com/CrowdStrike/falconpy/wiki/scheduled-reports#scheduled_reports_get)<BR>[report_executions_query](https://github.com/CrowdStrike/falconpy/wiki/report-executions#report_executions_query)
## USAGE
### List the first five scheduled report IDs that match a filtered search
```powershell
Get-FalconScheduledReport -Filter "created_on:<'2021-09-15'+status:'ACTIVE'+type:['hosts','spotlight_remediations']" -Limit 5 [-Detailed]
```
### Retrieve details about a scheduled report
```powershell
Get-FalconScheduledReport -Id <id>, <id>
```
### List the first five scheduled report execution IDs that match a filtered search
```powershell
Get-FalconScheduledReport -Filter "created_on:<'2021-10-01'+type:['hosts','dashboard']" -Limit 5 -Sort created_on.desc -Execution [-Detailed]
```
### Retrieve details about a scheduled report execution
```powershell
Get-FalconScheduledReport -Id <id>, <id> -Execution
```

_2023-04-25: PSFalcon v2.2.5_
