# Get-FalconScript
## SYNOPSIS
Search for custom Real-time Response scripts
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Script identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`100`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconScript [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScript -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /real-time-response/entities/scripts/v2
GET /real-time-response/queries/scripts/v1
```
### falconpy
[RTR_ListScripts](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListScripts)<BR>[RTR_GetScriptsV2](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_GetScriptsV2)
## USAGE
### Find scripts
```powershell
Get-FalconScript [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
