# Get-FalconIoaGroup
## SYNOPSIS
Search for custom Indicator of Attack rule groups
## DESCRIPTION
Requires 'Custom IOA rules: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Rule group identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`created_on`<BR>`description`<BR>`enabled`<BR>`modified_on`<BR>`name`<BR>`platform`<BR>`rules.action_label`<BR>`rules.name`<BR>`rules.description`<BR>`rules.pattern_severity`<BR>`rules.ruletype_name`<BR>`rules.enabled`||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`created_by.asc`<BR>`created_by.desc`<BR>`created_on.asc`<BR>`created_on.desc`<BR>`description.asc`<BR>`description.desc`<BR>`enabled.asc`<BR>`enabled.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`modified_on.asc`<BR>`modified_on.desc`<BR>`name.asc`<BR>`name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIoaGroup [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoaGroup -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoaGroup [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ioarules/entities/rule-groups/v1
GET /ioarules/queries/rule-groups/v1
GET /ioarules/queries/rule-groups-full/v1
```
### falconpy
[query_rule_groupsMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#query_rule_groupsMixin0)<BR>[get_rule_groupsMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#get_rule_groupsMixin0)<BR>[query_rule_groups_full](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#query_rule_groups_full)
## USAGE
### Find custom IOA rule groups
```powershell
Get-FalconIoaGroup [-Detailed]
```
### Find custom IOA rule groups matching a query
```powershell
Get-FalconIoaGroup -Filter "name:'updatedRuleGroup'+platform:'mac'" -Detailed
```
### Find custom IOA rule group identifiers matching a query
```powershell
Get-FalconIoaGroup -Filter "name:'updatedRuleGroup'+platform:'mac'"
```

_2023-04-25: PSFalcon v2.2.5_
