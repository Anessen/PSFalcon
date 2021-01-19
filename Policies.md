**NOTE**: The commands involved with Sensor Update, Device Control, Firewall and Response policies are nearly identical to those used for Prevention policies. The primary difference is how the `-Settings` parameter is formatted.

## Manage Policies

### Create a Prevention policy

```powershell
$Settings = @(
    @{
        id = "AdditionalUserModeData"
        value = @{
            enabled = $true
        }
    },
    @{
        id = "EndUserNotifications"
        value = @{
            enabled = $true
        }
    },
    @{
        id = "CloudAntiMalware"
        value = @{
            detection = "MODERATE"
            prevention = "MODERATE"
        }
    }
)
New-FalconPreventionPolicy -PlatformName Windows -Name "Demo Policy" -Description "This is a demo policy" -Settings $Settings
```

### Assign a host group to a Prevention policy

```powershell
Invoke-FalconPreventionPolicyAction -ActionName add-host-group -Id <id> -GroupId <id>
```

### Get all Prevention policies

```powershell
Get-FalconPreventionPolicy -All [-Detailed]
```

### Set Prevention policy precedence

```powershell
Set-FalconPreventionPrecedence -PlatformName Windows -Ids <id>, <id>
```

## Manage Machine Learning exclusions

### Create Machine Learning exclusions

```powershell
New-FalconMLExclusion -Value '/foo' -ExcludedFrom blocking, extraction -GroupIds all -Comment 'creating foo'
```

### Find Machine Learning exclusions

```powershell
Get-FalconMLExclusion [-Detailed] [-All]
```

### Modify Machine Learning exclusions

```powershell
Edit-FalconMLExclusion -Id <id> -Value '/foo*'
```

### Delete Machine Learning exclusions

```powershell
Remove-FalconMLExclusion -Ids <id>, <id>
```

## Manage Sensor Visibility exclusions

### Create Sensor Visibility exclusions

```powershell
New-FalconSVExclusion -Value '/foo' -GroupIds all -Comment 'creating'
```

### Find Sensor Visibility exclusions

```powershell
Get-FalconSVExclusion [-Detailed] [-All]
```

### Modify Sensor Visibility exclusions

```powershell
Edit-FalconSVExclusion -Id <id> -Value '/foochanged*'
```

### Delete Sensor Visibility exclusions

```powershell
Remove-FalconSVExclusion -Ids <id>, <id>
```
## Manage IOA exclusions

### Modify IOA exclusions

```powershell
Edit-FalconIOAExclusion -Id <id> -ImagePath '.*\\Windows\\System32\\choice1\.exe'
```

### Find IOA exclusions

```powershell
Get-FalconIOAExclusion [-Detailed]
```

### Delete IOA exclusions

```powershell
Remove-FalconIOAExclusion -Ids <id>, <id>
```

## Custom IOA Rules

### Find custom IOA rule types

```powershell
Get-FalconIOAType [-Detailed]
```

### Find custom IOA severities

```powershell
Get-FalconIOASeverity [-Detailed]
```

### Find custom IOA platforms

```powershell
Get-FalconIOAPlatform [-Detailed]
```

### Create custom IOA rule groups

```powershell
New-FalconIOAGroup -Platform mac -Name newRuleGroup -Description "My new mac rule group"
```

### Modify custom IOA rule groups

```powershell
$Current = Get-FalconIOAGroup -Filter "name:'newRuleGroup'" -Detailed

Edit-FalconIOAGroup -Id $Current.id -Name "updatedRuleGroup" -Enabled $true -RulegroupVersion $Current.version -Description "My updated mac rule group" -Comment "Updated using PSFalcon"
```

### Find custom IOA rule groups

```powershell
Get-FalconIOAGroup [-Detailed]
```

### Delete custom IOA rule groups

```powershell
Remove-FalconIOAGroup -Ids <id>, <id>
```

### Create custom IOA rules

```powershell
$Group = Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'" -Detailed

$FieldValues = @{
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

New-FalconIOARule -RulegroupId $Group.id -Name "BugRule" -PatternSeverity critical -RuletypeId 5 -DispositionId 30 -FieldValues $FieldValues
```

### Modify custom IOA rules

```powershell
$Group = Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'" -Detailed

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

Edit-FalconIOARule -RulegroupId $Group.id -RulegroupVersion $Group.version -RuleUpdates $RuleUpdates -Comment "Updated using PSFalcon"
```

### Find custom IOA rules

```powershell
Get-FalconIOARule [-Detailed]
```

### Delete custom IOA rules

```powershell
Remove-FalconIOARule -RulegroupId <id> -Ids <id>, <id>
```

### Validating field values

```powershell
$Fields = @(
    @{
        label = 'Grandparent Image Filename'
        name = 'GrandparentImageFilename'
        type = 'excludable'
        values = @(
            @{
                label = 'include'
                value = '.+attacker.exe'
            }
        )
    }
)

Test-FalconIOARule -Fields $Fields
```

### Find custom IOA rule groups matching a query

```powershell
Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'+platform:'mac'" -Detailed
```

### Find custom IOA rule group identifiers matching a query

```powershell
Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'+platform:'mac'"
```

### Find a custom IOA rule identifier by name within a rule group

```powershell
Get-FalconIOARule -Filter "id:'<id>'+rules.name:'BugRule'" [-Detailed] [-All]
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/85/detection-and-prevention-policies-apis)