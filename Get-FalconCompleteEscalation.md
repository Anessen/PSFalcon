# Get-FalconCompleteEscalation
## SYNOPSIS
Search for Falcon Complete escalations
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
Get-FalconCompleteEscalation [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falcon-complete-dashboards/queries/escalations/v1
```
### falconpy
[QueryEscalationsFilter](https://github.com/CrowdStrike/falconpy/wiki/falcon-complete-dashboard#QueryEscalationsFilter)
## USAGE
### Search for Falcon Complete escalation identifiers
```powershell
Get-FalconCompleteEscalation [-All]
```
### Display the total number of Falcon Complete escalation tickets
```powershell
Get-FalconCompleteEscalation -Total
```

_2023-04-25: PSFalcon v2.2.5_
