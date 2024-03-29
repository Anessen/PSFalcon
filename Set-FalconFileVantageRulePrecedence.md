# Set-FalconFileVantageRulePrecedence
## SYNOPSIS
Set FileVantage rule precedence within a rule group
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|RuleGroupId|String|FileVantage rule group identifier||||||
|Id|String[]|FileVantage rule identifiers in precedence order||||X||
## SYNTAX
```powershell
Set-FalconFileVantageRulePrecedence [-RuleGroupId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/rule-groups-rule-precedence/v1
```
### falconpy
[updateRuleGroupPrecedence](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updateRuleGroupPrecedence)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
