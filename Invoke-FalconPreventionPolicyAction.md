# Invoke-FalconPreventionPolicyAction
## SYNOPSIS
Perform actions on Prevention policies
## DESCRIPTION
Requires 'Prevention Policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add-host-group`<BR>`add-rule-group`<BR>`disable`<BR>`enable`<BR>`remove-host-group`<BR>`remove-rule-group`|||
|GroupId|String|Host or rule group identifier||||||
|Id|String|Policy identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconPreventionPolicyAction [-Name] <String> [[-GroupId] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/prevention-actions/v1
```
### falconpy
[performPreventionPoliciesAction](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#performPreventionPoliciesAction)
## USAGE
### Assign host groups to policies
```powershell
Invoke-FalconPreventionPolicyAction -Name add-host-group -Id <policy_id> -GroupId <host_group_id>
```
```powershell
Get-FalconPreventionPolicy -Filter "name:'my_policy'" | Invoke-FalconPreventionPolicyAction -Name add-host-group -GroupId <host_group_id>
```

_2023-04-25: PSFalcon v2.2.5_
