# Get-FalconTailoredRule
## SYNOPSIS
Search for tailored intelligence rules
## DESCRIPTION
Requires 'Tailored Intelligence: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Tailored intelligence rule identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|String|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconTailoredRule [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconTailoredRule [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ti/rules/queries/rules/v2
POST /ti/rules/entities/rules/GET/v2
```
### falconpy
[QueryRules](https://github.com/CrowdStrike/falconpy/wiki/ti#QueryRules)<BR>[GetRulesEntities](https://github.com/CrowdStrike/falconpy/wiki/ti#GetRulesEntities)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
