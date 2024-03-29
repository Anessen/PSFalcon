# Edit-FalconIoaRule
## SYNOPSIS
Modify custom Indicator of Attack rules within a rule group
## DESCRIPTION
All fields are required (plus 'rulegroup_version') when making a rule group change. PSFalcon adds missing values
automatically using data from your existing rule group.

If an existing rule is submitted within 'rule_updates', it will be filtered to the required properties ('comment',
'description', 'disposition_id', 'enabled', 'field_values', 'instance_id', 'name', and 'pattern_severity')
including those under 'field_values' ('name', 'label', 'type' and 'values').

Requires 'Custom IOA rules: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Audit log comment||||||
|RuleUpdate|Object[]|An array of rule properties|||||X|
|RulegroupId|String|Rule group identifier|||||X|
## SYNTAX
```powershell
Edit-FalconIoaRule [[-Comment] <String>] [[-RuleUpdate] <Object[]>] [-RulegroupId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /ioarules/entities/rules/v1
```
### falconpy
[update_rules](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#update_rules)
## USAGE
### Modify custom IOA rules
```powershell
$Group = Get-FalconIoaGroup -Filter "name:'updatedRuleGroup'" -Detailed
$RuleUpdates = @(
    @{
        name = 'BugRule'
        pattern_severity = 'critical'
        enabled = $true
        description = 'Stops the bug'
        disposition_id = 30
        instance_id = '1'
        field_values = @(
            @{
                label = 'Grandparent Image Filename'
                name = 'GrandparentImageFilename'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.+updatebug.exe'
                    }
                )
            },
            @{
                label = 'Grandparent Command Line'
                name = 'GrandparentCommandLine'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            },
            @{
                label = 'Parent Image Filename'
                name = 'ParentImageFilename'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            },
            @{
                label = 'Parent Command Line'
                name = 'ParentCommandLine'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            },
            @{
                label = 'Image Filename'
                name = 'ImageFilename'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            },
            @{
                label = 'Command Line'
                name = 'CommandLine'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            }
        )
    }
)
Edit-FalconIoaRule -RulegroupId $Group.id -RulegroupVersion $Group.version -RuleUpdate $RuleUpdates -Comment 'Updated using PSFalcon'
```
### Enable rules in an existing group
```powershell
$Group = Get-FalconIoaGroup -Filter "name:'my group'" -Detailed
@($Group.rules).foreach{ $_.enabled = $true }
Edit-FalconIoaGroup -RulegroupId $Group.id -RuleUpdate $Group.rules
```

_2023-04-25: PSFalcon v2.2.5_
