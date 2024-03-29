# Get-FalconReport
## SYNOPSIS
Search for Falcon Intelligence Sandbox reports
## DESCRIPTION
Requires 'Sandbox (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Report identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Summary|Switch|Return a summary version||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconReport [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReport -Id <String[]> -Summary [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReport -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falconx/entities/reports/v1
GET /falconx/entities/report-summaries/v1
GET /falconx/queries/reports/v1
```
### falconpy
[QueryReports](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#QueryReports)<BR>[GetSummaryReports](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#GetSummaryReports)<BR>[GetReports](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#GetReports)
## USAGE
### View a sandbox report
```powershell
Get-FalconReport -Id <id>, <id>
```
### View a summary-level sandbox report
```powershell
Get-FalconReport -Id <id>, <id> -Summary
```
_See [New-FalconSubmission](New-FalconSubmission)._

_2023-04-25: PSFalcon v2.2.5_
