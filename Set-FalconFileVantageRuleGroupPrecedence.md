# Set-FalconFileVantageRuleGroupPrecedence
## SYNOPSIS
Set rule group precedence within FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PolicyId|String|FileVantage policy identifier||||||
|Id|String[]|FileVantage rule group identifiers in precedence order||||X||
## SYNTAX
```powershell
Set-FalconFileVantageRuleGroupPrecedence [-PolicyId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/policies-rule-groups/v1
```
### falconpy
[updatePolicyRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updatePolicyRuleGroups)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
