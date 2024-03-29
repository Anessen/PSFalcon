# Get-FalconIncident
## SYNOPSIS
Search for incidents
## DESCRIPTION
Requires 'Incidents: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Incident identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`assigned_to_name`<BR>`description`<BR>`end`<BR>`fine_score`<BR>`host_ids`<BR>`lm_host_ids`<BR>`lm_hosts_capped`<BR>`modified_timestamp`<BR>`name`<BR>`start`<BR>`state`<BR>`status`<BR>`tags`<BR>`users`||||||
|Sort|String|Property and direction to sort results|||`assigned_to.asc`<BR>`assigned_to.desc`<BR>`assigned_to_name.asc`<BR>`assigned_to_name.desc`<BR>`end.asc`<BR>`end.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`<BR>`sort_score.asc`<BR>`sort_score.desc`<BR>`start.asc`<BR>`start.desc`<BR>`state.asc`<BR>`state.desc`<BR>`status.asc`<BR>`status.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIncident [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIncident -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /incidents/queries/incidents/v1
POST /incidents/entities/incidents/GET/v1
```
### falconpy
[QueryIncidents](https://github.com/CrowdStrike/falconpy/wiki/incidents#QueryIncidents)<BR>[GetIncidents](https://github.com/CrowdStrike/falconpy/wiki/incidents#GetIncidents)
## USAGE
### Find incidents
```powershell
Get-FalconIncident [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
