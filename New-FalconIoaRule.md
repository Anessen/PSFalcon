# New-FalconIoaRule
## SYNOPSIS
Create a custom Indicator of Attack rule within a rule group
## DESCRIPTION
'RuleTypeId' and 'DispositionId' values can be found using 'Get-FalconIoaType -Detailed' under the 'id' and
'disposition_map' properties.

Requires 'Custom IOA rules: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Rule name|||||X|
|PatternSeverity|String|Rule severity|||`critical`<BR>`high`<BR>`medium`<BR>`low`<BR>`informational`||X|
|RuletypeId|String|Rule type|||`1`<BR>`2`<BR>`5`<BR>`6`<BR>`9`<BR>`10`<BR>`11`<BR>`12`||X|
|DispositionId|Int32|Disposition identifier [10: Monitor, 20: Detect, 30: Block]|||`10`<BR>`20`<BR>`30`||X|
|FieldValue|Object[]|An array of rule properties|||||X|
|Description|String|Rule description|||||X|
|Comment|String|Audit log comment|||||X|
|RulegroupId|String|Rule group identifier|||||X|
## SYNTAX
```powershell
New-FalconIoaRule [-Name] <String> [-PatternSeverity] <String> [-RuletypeId] <String> [-DispositionId] <Int32> [-FieldValue] <Object[]> [[-Description] <String>] [[-Comment] <String>] [-RulegroupId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /ioarules/entities/rules/v1
```
### falconpy
[create_rule](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#create_rule)
## USAGE
### Create custom IOA rules
```powershell
$Group = Get-FalconIoaGroup -Filter "name:'updatedRuleGroup'" -Detailed
$FieldValue = @{
    label = 'Grandparent Image Filename'
    name = 'GrandparentImageFilename'
    type = 'excludable'
    values = @(
        @{
            label = 'include'
            value = '.+bug.exe'
        }
    )
}
New-FalconIoaRule -RulegroupId $Group.id -Name 'BugRule' -PatternSeverity critical -RuletypeId 5 -DispositionId 30 -FieldValue $FieldValue
```

_2023-04-25: PSFalcon v2.2.5_
