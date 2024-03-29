# Get-FalconLibraryScript
## SYNOPSIS
Search for scripts in the 'falconscript' library
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`categories`<BR>`modified_timestamp`<BR>`name`<BR>`workflow_enabled`||||||
|Sort|String|Property and direction to sort results|||`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconLibraryScript [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconLibraryScript -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /real-time-response/entities/falcon-scripts/v1
GET /real-time-response/queries/falcon-scripts/v1
```
### falconpy
[RTR_ListFalconScripts](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListFalconScripts)<BR>[RTR_GetFalconScripts](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_GetFalconScripts)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
