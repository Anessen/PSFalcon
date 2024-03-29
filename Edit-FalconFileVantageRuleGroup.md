# Edit-FalconFileVantageRuleGroup
## SYNOPSIS
Modify FileVantage rule groups
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|FileVantage rule group identifier||||X|X|
|Name|String|Rule group name|`1`|`100`||||
|Description|String|Rule group description||`500`||||
## SYNTAX
```powershell
Edit-FalconFileVantageRuleGroup -Id <String> [[-Name] <String>] [[-Description] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/rule-groups/v1
```
### falconpy
[updateRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updateRuleGroups)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
