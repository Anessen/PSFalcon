# Invoke-FalconFirewallPolicyAction
## SYNOPSIS
Perform actions on Falcon Firewall Management policies
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add-host-group`<BR>`disable`<BR>`enable`<BR>`remove-host-group`|||
|GroupId|String|Host group identifier||||||
|Id|String|Policy identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconFirewallPolicyAction [-Name] <String> [[-GroupId] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/firewall-actions/v1
```
### falconpy
[performFirewallPoliciesAction](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#performFirewallPoliciesAction)
## USAGE
### Enabling firewall policies
```powershell
Invoke-FalconFirewallPolicyAction -Name enable -Id <id>
```
### Assigning host groups to a policy
```powershell
Invoke-FalconFirewallPolicyAction -Name add-host-group -Id <id> -GroupId <id>
```
### Disabling firewall policies
```powershell
Invoke-FalconFirewallPolicyAction -Name disable -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
