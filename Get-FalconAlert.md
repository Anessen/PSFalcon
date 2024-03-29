# Get-FalconAlert
## SYNOPSIS
Search for alerts
## DESCRIPTION
Requires 'Alerts: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Alert identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`10000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconAlert [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAlert -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /alerts/queries/alerts/v1
POST /alerts/entities/alerts/v2
```
### falconpy
[GetQueriesAlertsV1](https://github.com/CrowdStrike/falconpy/wiki/alerts#GetQueriesAlertsV1)<BR>[PostEntitiesAlertsV2](https://github.com/CrowdStrike/falconpy/wiki/alerts#PostEntitiesAlertsV2)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
