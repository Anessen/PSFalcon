# New-FalconFileVantageRuleGroup
## SYNOPSIS
Create FileVantage rule groups
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Type|String|Rule group type|||`LinuxFiles`<BR>`MacFiles`<BR>`WindowsFiles`<BR>`WindowsRegistry`||X|
|Name|String|Rule group name|`1`|`100`|||X|
|Description|String|Rule group description||`500`|||X|
## SYNTAX
```powershell
New-FalconFileVantageRuleGroup [-Type] <String> [-Name] <String> [[-Description] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /filevantage/entities/rule-groups/v1
```
### falconpy
[createRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#createRuleGroups)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
