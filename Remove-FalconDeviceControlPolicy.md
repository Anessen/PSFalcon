# Remove-FalconDeviceControlPolicy
## SYNOPSIS
Remove Falcon Device Control policies
## DESCRIPTION
Requires 'Device control policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconDeviceControlPolicy [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/device-control/v1
```
### falconpy
[deleteDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#deleteDeviceControlPolicies)
## USAGE
### Delete a policy
```powershell
Remove-FalconDeviceControlPolicy -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
