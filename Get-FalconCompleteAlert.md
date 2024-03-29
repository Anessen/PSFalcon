# Get-FalconCompleteAlert
## SYNOPSIS
Search for Falcon Complete alerts
## DESCRIPTION
Requires 'Falcon Complete Dashboards: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|String|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconCompleteAlert [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falcon-complete-dashboards/queries/alerts/v1
```
### falconpy
[QueryAlertIdsByFilter](https://github.com/CrowdStrike/falconpy/wiki/falcon-complete-dashboard#QueryAlertIdsByFilter)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
