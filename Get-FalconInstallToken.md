# Get-FalconInstallToken
## SYNOPSIS
Search for installation tokens
## DESCRIPTION
Requires 'Installation tokens: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Installation token identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`1000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconInstallToken [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconInstallToken -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /installation-tokens/entities/tokens/v1
GET /installation-tokens/queries/tokens/v1
```
### falconpy
[tokens_query](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#tokens_query)<BR>[tokens_read](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#tokens_read)
## USAGE
### Find installation tokens
```powershell
Get-FalconInstallToken [-Detailed] [-All]
```
### Get information about an installation token
```powershell
Get-FalconInstallToken -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
