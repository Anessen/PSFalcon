# Remove-FalconIoaGroup
## SYNOPSIS
Remove custom Indicator of Attack rule groups
## DESCRIPTION
Requires 'Custom IOA rules: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Audit log comment||||||
|Id|String[]|Rule group identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconIoaGroup [[-Comment] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /ioarules/entities/rule-groups/v1
```
### falconpy
[delete_rule_groupsMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#delete_rule_groupsMixin0)
## USAGE
### Delete custom IOA rule groups
```powershell
Remove-FalconIoaGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
