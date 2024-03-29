# Remove-FalconFileVantageRule
## SYNOPSIS
Remove FileVantage rules from rule groups
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|RuleGroupId|String|FileVantage rule group identifier||||||
|Id|String[]|FileVantage rule identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFileVantageRule [-RuleGroupId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /filevantage/entities/rule-groups-rules/v1
```
### falconpy
[deleteRules](https://github.com/CrowdStrike/falconpy/wiki/filevantage#deleteRules)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
