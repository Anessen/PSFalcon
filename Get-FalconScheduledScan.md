# Get-FalconScheduledScan
## SYNOPSIS
Search for scheduled scans
## DESCRIPTION
Requires 'On-demand scans (ODS): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Scheduled scan identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`id\|asc`<BR>`id\|desc`<BR>`description.keyword\|asc`<BR>`description.keyword\|desc`<BR>`status\|asc`<BR>`status\|desc`<BR>`schedule.start_timestamp\|asc`<BR>`schedule.start_timestamp\|desc`<BR>`schedule.interval\|asc`<BR>`schedule.interval\|desc`<BR>`created_on\|asc`<BR>`created_on\|desc`<BR>`created_by\|asc`<BR>`created_by\|desc`<BR>`last_updated\|asc`<BR>`last_updated\|desc`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconScheduledScan [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScheduledScan -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ods/entities/scheduled-scans/v1
GET /ods/queries/scheduled-scans/v1
```
### falconpy
[query_scheduled_scans](https://github.com/CrowdStrike/falconpy/wiki/ods#query_scheduled_scans)<BR>[get_scheduled_scans_by_scan_ids](https://github.com/CrowdStrike/falconpy/wiki/ods#get_scheduled_scans_by_scan_ids)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
