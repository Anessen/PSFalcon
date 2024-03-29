# Invoke-FalconResponsePolicyAction
## SYNOPSIS
Perform actions on Real-time Response policies
## DESCRIPTION
Requires 'Response policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add-host-group`<BR>`disable`<BR>`enable`<BR>`remove-host-group`|||
|GroupId|String|Host group identifier||||||
|Id|String|Policy identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconResponsePolicyAction [-Name] <String> [[-GroupId] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/response-actions/v1
```
### falconpy
[performRTResponsePoliciesAction](https://github.com/CrowdStrike/falconpy/wiki/response-policies#performRTResponsePoliciesAction)
## USAGE
### Assign host groups to a policy
```powershell
Invoke-FalconResponsePolicyAction -Name add-host-group -Id <id> -GroupId <id>
```
### Enable a policy
```powershell
Invoke-FalconResponsePolicyAction -Name enable -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
