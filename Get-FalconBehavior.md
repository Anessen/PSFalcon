# Get-FalconBehavior
## SYNOPSIS
Search for behaviors
## DESCRIPTION
Requires 'Incidents: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Behavior identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`aid`<BR>`incident_id`<BR>`pattern_id`<BR>`template_instance_id`<BR>`timestamp`||||||
|Sort|String|Property and direction to sort results|||`timestamp.asc`<BR>`timestamp.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconBehavior [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconBehavior -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /incidents/queries/behaviors/v1
POST /incidents/entities/behaviors/GET/v1
```
### falconpy
[QueryBehaviors](https://github.com/CrowdStrike/falconpy/wiki/incidents#QueryBehaviors)<BR>[GetBehaviors](https://github.com/CrowdStrike/falconpy/wiki/incidents#GetBehaviors)
## USAGE
### Find behaviors
```powershell
Get-FalconBehavior [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
