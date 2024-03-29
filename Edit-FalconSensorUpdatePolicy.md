# Edit-FalconSensorUpdatePolicy
## SYNOPSIS
Modify Sensor Update policies
## DESCRIPTION
Requires 'Sensor update policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to modify in a single request||||X||
|Id|String|Policy identifier||||||
|Name|String|Policy name||||||
|Description|String|Policy description||||||
|Setting|Object|Policy settings||||||
## SYNTAX
```powershell
Edit-FalconSensorUpdatePolicy [-Id] <String> [[-Name] <String>] [[-Description] <String>] [[-Setting] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconSensorUpdatePolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/sensor-update/v2
```
### falconpy
[updateSensorUpdatePoliciesV2](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#updateSensorUpdatePoliciesV2)
## USAGE
### Change the build version of a sensor update policy
```powershell
$Id = Get-FalconSensorUpdatePolicy -Filter "name:'my_policy'"
Edit-FalconSensorUpdatePolicy -Id $Id -Setting @{ build = '12345' }
```

_See [Get-FalconBuild](Get-FalconBuild)._

_See [Modify the build of a Sensor Update policy by name](https://github.com/CrowdStrike/psfalcon/blob/master/samples/policies/modify-the-build-of-a-sensor-update-policy-by-name.ps1)._

_2023-04-25: PSFalcon v2.2.5_
