# Remove-FalconFirewallPolicy
## SYNOPSIS
Remove Falcon Firewall Management policies
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFirewallPolicy [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/firewall/v1
```
### falconpy
[deleteFirewallPolicies](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#deleteFirewallPolicies)
## USAGE
### Deleting firewall policies
```powershell
Remove-FalconFirewallPolicy -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
