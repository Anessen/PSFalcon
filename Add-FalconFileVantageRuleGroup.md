# Add-FalconFileVantageRuleGroup
## SYNOPSIS
Add rule groups to FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PolicyId|String|FileVantage policy identifier||||||
|Id|String[]|FileVantage rule group identifier||||X|X|
## SYNTAX
```powershell
Add-FalconFileVantageRuleGroup [-PolicyId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/policies-rule-groups/v1
```
### falconpy
[updatePolicyRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updatePolicyRuleGroups)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
