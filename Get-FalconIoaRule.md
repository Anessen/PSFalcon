# Get-FalconIoaRule
## SYNOPSIS
Search for custom Indicator of Attack rules
## DESCRIPTION
Requires 'Custom IOA rules: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Rule identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`created_on`<BR>`description`<BR>`enabled`<BR>`modified_on`<BR>`name`<BR>`platform`<BR>`rules.action_label`<BR>`rules.name`<BR>`rules.description`<BR>`rules.pattern_severity`<BR>`rules.ruletype_name`<BR>`rules.enabled`||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`rules.created_by.asc`<BR>`rules.created_by.desc`<BR>`rules.created_on.asc`<BR>`rules.created_on.desc`<BR>`rules.current_version.action_label.asc`<BR>`rules.current_version.action_label.desc`<BR>`rules.current_version.description.asc`<BR>`rules.current_version.description.desc`<BR>`rules.current_version.modified_by.asc`<BR>`rules.current_version.modified_by.desc`<BR>`rules.current_version.modified_on.asc`<BR>`rules.current_version.modified_on.desc`<BR>`rules.current_version.name.asc`<BR>`rules.current_version.name.desc`<BR>`rules.current_version.pattern_severity.asc`<BR>`rules.current_version.pattern_severity.desc`<BR>`rules.enabled.asc`<BR>`rules.enabled.desc`<BR>`rules.ruletype_name.asc`<BR>`rules.ruletype_name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIoaRule [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoaRule -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ioarules/queries/rules/v1
POST /ioarules/entities/rules/GET/v1
```
### falconpy
[query_rulesMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#query_rulesMixin0)<BR>[get_rules_get](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#get_rules_get)
## USAGE
### Find custom IOA rules
```powershell
Get-FalconIoaRule [-Detailed]
```
### Find a custom IOA rule identifier by name within a rule group
```powershell
Get-FalconIoaRule -Filter "id:'<id>'+rules.name:'BugRule'" [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
