# Get-FalconPutFile
## SYNOPSIS
Search for Real-time Response 'put' files
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|'Put' file identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`100`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconPutFile [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconPutFile -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /real-time-response/entities/put-files/v2
GET /real-time-response/queries/put-files/v1
```
### falconpy
[RTR_ListPut_Files](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListPut_Files)<BR>[RTR_GetPut_FilesV2](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_GetPut_FilesV2)
## USAGE
### Find 'put' files
```powershell
Get-FalconPutFile [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
