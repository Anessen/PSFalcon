# Get-FalconFileVantageRule
## SYNOPSIS
List FileVantage rules within a rule group
## DESCRIPTION
Requires 'Falcon FileVantage: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|RuleGroupId|String|FileVantage rule group identifier||||||
|Id|String[]|FileVantage rule identifier||||X|X|
## SYNTAX
```powershell
Get-FalconFileVantageRule [-RuleGroupId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /filevantage/entities/rule-groups-rules/v1
```
### falconpy
[getRules](https://github.com/CrowdStrike/falconpy/wiki/filevantage#getRules)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
