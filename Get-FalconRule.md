# Get-FalconRule
## SYNOPSIS
Search for Falcon Intelligence rulesets
## DESCRIPTION
Requires 'Rules (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Ruleset identifier||||X|X|
|Type|String|Ruleset type|||`snort-suricata-master`<BR>`snort-suricata-update`<BR>`snort-suricata-changelog`<BR>`yara-master`<BR>`yara-update`<BR>`yara-changelog`<BR>`common-event-format`<BR>`netwitness`|||
|Name|String[]|Ruleset name||||||
|Description|String[]|Ruleset description||||||
|Tag|String[]|Ruleset tag||||||
|MinCreatedDate|Int32|Filter results to those created on or after a date||||||
|MaxCreatedDate|String|Filter results to those created on or before a date||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconRule [-Type] <String> [[-Name] <String[]>] [[-Description] <String[]>] [[-Tag] <String[]>] [[-MinCreatedDate] <Int32>] [[-MaxCreatedDate] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconRule -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/entities/rules/v1
GET /intel/queries/rules/v1
```
### falconpy
[QueryIntelRuleIds](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryIntelRuleIds)<BR>[GetIntelRuleEntities](https://github.com/CrowdStrike/falconpy/wiki/intel#GetIntelRuleEntities)
## USAGE
### Search for a rule set
```powershell
Get-FalconRule -Type yara-master -MinCreatedDate 1509494400 -Limit 3
```
### Get information about a specific rule set
```powershell
Get-FalconRule -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
