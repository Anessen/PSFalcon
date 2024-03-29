# New-FalconPreventionPolicy
## SYNOPSIS
Create Prevention policies
## DESCRIPTION
Requires 'Prevention Policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to create in a single request||||X||
|Name|String|Policy name||||||
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`<BR>`iOS`<BR>`Android`|||
|Description|String|Policy description||||||
|Setting|Object[]|An array of policy settings||||||
## SYNTAX
```powershell
New-FalconPreventionPolicy [-Name] <String> [-PlatformName] <String> [[-Description] <String>] [[-Setting] <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconPreventionPolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/prevention/v1
```
### falconpy
[createPreventionPolicies](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#createPreventionPolicies)
## USAGE
### Create a policy
```powershell
$Setting = @(
    @{
        id = 'AdditionalUserModeData'
        value = @{ enabled = $true }
    },
    @{
        id = 'EndUserNotifications'
        value = @{ enabled = $true }
    },
    @{
        id = 'CloudAntiMalware'
        value = @{ detection = 'MODERATE'; prevention = 'MODERATE' }
    }
)
New-FalconPreventionPolicy -PlatformName Windows -Name 'Demo Policy' -Description 'This is a demo policy' -Setting $Setting
```

_2023-04-25: PSFalcon v2.2.5_
