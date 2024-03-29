# Remove-FalconFileVantageRuleGroup
## SYNOPSIS
Remove FileVantage rule groups or unassign them from policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PolicyId|String|FileVantage policy identifier, used when unassigning rule groups from a policy||||||
|Id|String[]|FileVantage rule group identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFileVantageRuleGroup [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Remove-FalconFileVantageRuleGroup [-PolicyId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /filevantage/entities/rule-groups/v1
PATCH /filevantage/entities/policies-rule-groups/v1
```
### falconpy
[deleteRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#deleteRuleGroups)<BR>[updatePolicyRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updatePolicyRuleGroups)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
