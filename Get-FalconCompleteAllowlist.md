# Get-FalconCompleteAllowlist
## SYNOPSIS
Search for Falcon Complete Allowlist tickets
## DESCRIPTION
Requires 'Falcon Complete Dashboards: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconCompleteAllowlist [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falcon-complete-dashboards/queries/allowlist/v1
```
### falconpy
[QueryAllowListFilter](https://github.com/CrowdStrike/falconpy/wiki/falcon-complete-dashboard#QueryAllowListFilter)
## USAGE
### Search for Falcon Complete allowlist identifiers
```powershell
Get-FalconCompleteAllowlist [-All]
```
### Display the total number of Falcon Complete allowlist tickets
```powershell
Get-FalconCompleteAllowlist -Total
```

_2023-04-25: PSFalcon v2.2.5_
