# Edit-FalconPreventionPolicy
## SYNOPSIS
Modify Prevention policies
## DESCRIPTION
Requires 'Prevention Policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to modify in a single request||||X||
|Id|String|Policy identifier||||||
|Name|String|Policy name||||||
|Description|String|Policy description||||||
|Setting|Object[]|Policy settings||||||
## SYNTAX
```powershell
Edit-FalconPreventionPolicy [-Id] <String> [[-Name] <String>] [[-Description] <String>] [[-Setting] <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconPreventionPolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/prevention/v1
```
### falconpy
[updatePreventionPolicies](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#updatePreventionPolicies)
## USAGE
### Configure policy settings
```powershell
$Setting = @(
    @{
        id = 'AdditionalUserModeData'
        value = @{ enabled = $false }
        }
    )
Edit-FalconPreventionPolicy -Id <id> -Name 'AV Policy' -Setting $Setting
```

_2023-04-25: PSFalcon v2.2.5_
