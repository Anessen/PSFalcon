# Remove-FalconIoaRule
## SYNOPSIS
Remove custom Indicator of Attack rules from rule groups
## DESCRIPTION
Requires 'Custom IOA rules: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Audit log comment||||||
|RuleGroupId|String|Rule group identifier|||||X|
|Id|String[]|Rule identifier|||||X|
## SYNTAX
```powershell
Remove-FalconIoaRule [[-Comment] <String>] [-RuleGroupId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /ioarules/entities/rules/v1
```
### falconpy
[delete_rules](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#delete_rules)
## USAGE
### Delete custom IOA rules
```powershell
Remove-FalconIoaRule -RulegroupId <id> -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
