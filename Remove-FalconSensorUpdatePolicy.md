# Remove-FalconSensorUpdatePolicy
## SYNOPSIS
Remove Sensor Update policies
## DESCRIPTION
Requires 'Sensor update policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconSensorUpdatePolicy [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/sensor-update/v1
```
### falconpy
[deleteSensorUpdatePolicies](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#deleteSensorUpdatePolicies)
## USAGE
### Delete a policy
```powershell
Remove-FalconSensorUpdatePolicy -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
