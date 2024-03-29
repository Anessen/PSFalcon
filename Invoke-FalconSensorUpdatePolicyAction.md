# Invoke-FalconSensorUpdatePolicyAction
## SYNOPSIS
Perform actions on Sensor Update policies
## DESCRIPTION
Requires 'Sensor update policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add-host-group`<BR>`disable`<BR>`enable`<BR>`remove-host-group`|||
|GroupId|String|Host group identifier||||||
|Id|String|Policy identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconSensorUpdatePolicyAction [-Name] <String> [[-GroupId] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/sensor-update-actions/v1
```
### falconpy
[performSensorUpdatePoliciesAction](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#performSensorUpdatePoliciesAction)
## USAGE
### Assigning host groups to a policy
```powershell
Invoke-FalconSensorUpdatePolicyAction -Name add-host-group -Id <id> -GroupId <id>
```
### Enabling a policy
```powershell
Invoke-FalconSensorUpdatePolicyAction -Name enable -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
