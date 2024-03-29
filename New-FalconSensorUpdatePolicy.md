# New-FalconSensorUpdatePolicy
## SYNOPSIS
Create Sensor Update policies
## DESCRIPTION
Requires 'Sensor update policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to create in a single request||||X||
|Name|String|Policy name||||||
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Description|String|Policy description||||||
|Setting|Object|Policy settings||||||
## SYNTAX
```powershell
New-FalconSensorUpdatePolicy [-Name] <String> [-PlatformName] <String> [[-Description] <String>] [[-Setting] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconSensorUpdatePolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/sensor-update/v2
```
### falconpy
[createSensorUpdatePoliciesV2](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#createSensorUpdatePoliciesV2)
## USAGE
### Creating a policy
```powershell
New-FalconSensorUpdatePolicy -PlatformName Windows -Name 'My Windows Sensor Policy' -Setting @{ build = '14105|Auto'; uninstall_protection = 'ENABLED' } -Description 'Upgrades Windows hosts to latest sensor'
```

_2023-04-25: PSFalcon v2.2.5_
