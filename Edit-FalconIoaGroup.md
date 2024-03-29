# Edit-FalconIoaGroup
## SYNOPSIS
Modify a custom Indicator of Attack rule group
## DESCRIPTION
All fields (plus 'rulegroup_version') are required when making a rule group change. PSFalcon adds missing values
automatically using data from your existing rule group.

Requires 'Custom IOA rules: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Rule group name|||||X|
|Enabled|Boolean|Rule group enablement status|||||X|
|Description|String|Rule group description|||||X|
|Comment|String|Audit log comment|||||X|
|Id|String|Rule group identifier|||||X|
## SYNTAX
```powershell
Edit-FalconIoaGroup [[-Name] <String>] [[-Enabled] <Boolean>] [[-Description] <String>] [[-Comment] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /ioarules/entities/rule-groups/v1
```
### falconpy
[update_rule_groupMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#update_rule_groupMixin0)
## USAGE
### Modify custom IOA rule groups
```powershell
$Current = Get-FalconIoaGroup -Filter "name:'newRuleGroup'" -Detailed
Edit-FalconIoaGroup -Id $Current.id -Name 'updatedRuleGroup' -Enabled $true -RulegroupVersion $Current.version -Description 'My updated mac rule group' -Comment 'Updated using PSFalcon'
```

_2023-04-25: PSFalcon v2.2.5_
