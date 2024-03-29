# Get-FalconDiscoverScanner
## SYNOPSIS
Search for Falcon Discover active discovery scanners
## DESCRIPTION
Requires 'Falcon Discover: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`100`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconDiscoverScanner [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /discover/queries/active-discovery-scanners/v1
```
### falconpy
[query_active_discovery_scanners](https://github.com/CrowdStrike/falconpy/wiki/discover#query_active_discovery_scanners)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
