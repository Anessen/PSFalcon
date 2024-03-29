# Invoke-FalconDeviceControlPolicyAction
## SYNOPSIS
Perform actions on Falcon Device Control policies
## DESCRIPTION
Requires 'Device control policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add-host-group`<BR>`disable`<BR>`enable`<BR>`remove-host-group`|||
|GroupId|String|Host group identifier||||||
|Id|String|Policy identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconDeviceControlPolicyAction [-Name] <String> [[-GroupId] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/device-control-actions/v1
```
### falconpy
[performDeviceControlPoliciesAction](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#performDeviceControlPoliciesAction)
## USAGE
### Assign host groups to a policy
```powershell
Invoke-FalconDeviceControlPolicyAction -Name add-host-group -Id <id> -GroupId <id>
```
### Enable the policy
```powershell
Invoke-FalconDeviceControlPolicyAction -Name enable -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
