# Get-FalconReplicatorField
## SYNOPSIS
Search for Falcon Data Replicator fields
## DESCRIPTION
Requires 'Falcon Data Replicator: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Falcon Data Replicator field identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`name`<BR>`description`<BR>`type`<BR>`universal`<BR>`values`||||||
|Sort|String|Property and direction to sort results|||`name.asc`<BR>`name.desc`<BR>`description.asc`<BR>`description.desc`<BR>`type.asc`<BR>`type.desc`<BR>`universal.asc`<BR>`universal.desc`<BR>`values.asc`<BR>`values.desc`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconReplicatorField [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReplicatorField -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fdr/entities/schema-fields/v1
GET /fdr/queries/schema-fields/v1
```
### falconpy
[fdrschema_queries_field_get](https://github.com/CrowdStrike/falconpy/wiki/fdr#fdrschema_queries_field_get)<BR>[fdrschema_entities_field_get](https://github.com/CrowdStrike/falconpy/wiki/fdr#fdrschema_entities_field_get)
## USAGE

_2023-04-28: PSFalcon v2.2.5_
