# Remove-FalconFirewallGroup
## SYNOPSIS
Remove Falcon Firewall Management rule groups
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Audit log comment||||||
|Id|String[]|Rule group identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFirewallGroup [[-Comment] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /fwmgr/entities/rule-groups/v1
```
### falconpy
[delete_rule_groups](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#delete_rule_groups)
## USAGE
### Deleting firewall rule groups
```powershell
Remove-FalconFirewallGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
