# New-FalconIoaGroup
## SYNOPSIS
Create a custom Indicator of Attack rule group
## DESCRIPTION
Requires 'Custom IOA rules: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Rule group name|||||X|
|Platform|String|Operating system platform|||`windows`<BR>`mac`<BR>`linux`||X|
|Description|String|Rule group description|||||X|
|Comment|String|Audit log comment|||||X|
## SYNTAX
```powershell
New-FalconIoaGroup [-Name] <String> [-Platform] <String> [[-Description] <String>] [[-Comment] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /ioarules/entities/rule-groups/v1
```
### falconpy
[create_rule_groupMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#create_rule_groupMixin0)
## USAGE
### Create custom IOA rule groups
```powershell
New-FalconIoaGroup -Platform mac -Name newRuleGroup -Description 'My new mac rule group'
```

_2023-04-25: PSFalcon v2.2.5_
