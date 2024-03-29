# Get-FalconReplicatorEvent
## SYNOPSIS
Search for Falcon Data Replicator events
## DESCRIPTION
Requires 'Falcon Data Replicator: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Falcon Data Replicator event identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`name`<BR>`description`<BR>`platform`<BR>`version`||||||
|Sort|String|Property and direction to sort results|||`name.asc`<BR>`name.desc`<BR>`description.asc`<BR>`description.desc`<BR>`platform.asc`<BR>`platform.desc`<BR>`version.asc`<BR>`version.desc`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconReplicatorEvent [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReplicatorEvent -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fdr/entities/schema-events/v1
GET /fdr/queries/schema-events/v1
```
### falconpy
[fdrschema_queries_event_get](https://github.com/CrowdStrike/falconpy/wiki/fdr#fdrschema_queries_event_get)<BR>[fdrschema_entities_event_get](https://github.com/CrowdStrike/falconpy/wiki/fdr#fdrschema_entities_event_get)
## USAGE

_2023-04-28: PSFalcon v2.2.5_
