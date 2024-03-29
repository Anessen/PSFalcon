# Get-FalconActor
## SYNOPSIS
Search for threat actors
## DESCRIPTION
Requires 'Actors (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Threat actor identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`actor_type`<BR>`capability`<BR>`capability.value`<BR>`created_date`<BR>`description`<BR>`ecrime_kill_chain.attribution`<BR>`ecrime_kill_chain.crimes`<BR>`ecrime_kill_chain.customers`<BR>`ecrime_kill_chain.marketing`<BR>`ecrime_kill_chain.monetization`<BR>`ecrime_kill_chain.services_offered`<BR>`ecrime_kill_chain.services_used`<BR>`ecrime_kill_chain.technical_tradecraft`<BR>`ecrime_kill_chain.victims`<BR>`first_activity_date`<BR>`group`<BR>`group.value`<BR>`id`<BR>`kill_chain.actions_and_objectives`<BR>`kill_chain.actions_on_objectives`<BR>`kill_chain.command_and_control`<BR>`kill_chain.delivery`<BR>`kill_chain.exploitation`<BR>`kill_chain.installation`<BR>`kill_chain.objectives`<BR>`kill_chain.reconnaissance`<BR>`kill_chain.weaponization`<BR>`known_as`<BR>`last_activity_date`<BR>`last_modified_date`<BR>`motivations`<BR>`motivations.value`<BR>`name`<BR>`origins`<BR>`origins.value`<BR>`region`<BR>`region.value`<BR>`short_description`<BR>`target_countries`<BR>`target_countries.value`<BR>`target_industries`<BR>`target_industries.value`||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`name\|asc`<BR>`name\|desc`<BR>`target_countries\|asc`<BR>`target_countries\|desc`<BR>`target_industries\|asc`<BR>`target_industries\|desc`<BR>`type\|asc`<BR>`type\|desc`<BR>`created_date\|asc`<BR>`created_date\|desc`<BR>`last_activity_date\|asc`<BR>`last_activity_date\|desc`<BR>`last_modified_date\|asc`<BR>`last_modified_date\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Field|String[]|Specific fields, or a predefined collection name surrounded by two underscores [default: __basic__]||||||
|Include|String|Include additional information|||`tactic_and_technique`|||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconActor [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconActor -Id <String[]> [[-Field] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconActor [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Field] <String[]>] [[-Include] <String>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/combined/actors/v1
GET /intel/entities/actors/v1
GET /intel/queries/actors/v1
```
### falconpy
[QueryIntelActorIds](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryIntelActorIds)<BR>[GetIntelActorEntities](https://github.com/CrowdStrike/falconpy/wiki/intel#GetIntelActorEntities)<BR>[QueryIntelActorEntities](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryIntelActorEntities)
## USAGE
### Search for a list of actor IDs
```powershell
Get-FalconActor -Filter "target_countries:'united states'+target_countries:'canada'+target_industries:'government'" [-All]
```
### Search for actors using a specific ID
```powershell
Get-FalconActor -Id <id>, <id>
```
### Search for detailed actor information
```powershell
Get-FalconActor -Filter "target_countries:'united states'+target_countries:'canada'+target_industries:'government'" -Limit 1 -Detailed
```

_2023-04-25: PSFalcon v2.2.5_
