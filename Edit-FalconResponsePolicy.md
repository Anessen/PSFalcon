# Edit-FalconResponsePolicy
## SYNOPSIS
Modify Real-time Response policies
## DESCRIPTION
Requires 'Response policies: Write'.
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
Edit-FalconResponsePolicy [-Id] <String> [[-Name] <String>] [[-Description] <String>] [[-Setting] <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconResponsePolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/response/v1
```
### falconpy
[updateRTResponsePolicies](https://github.com/CrowdStrike/falconpy/wiki/response-policies#updateRTResponsePolicies)
## USAGE
### Enable policy settings
```powershell
$Setting = @(
    @{
        id = 'RealTimeFunctionality'
        value = @{ enabled = $true }
    },
    @{
        id = 'CustomScripts'
        value = @{ enabled = $true }
    },
    @{
        id = 'GetCommand'
        value = @{ enabled = $true }
    },
    @{
        id = 'ExecCommand'
        value = @{ enabled = $true }
    }
)
Edit-FalconResponsePolicy -Id <id> -Setting $Setting
```

_2023-04-25: PSFalcon v2.2.5_
