# Get-FalconFirewallSetting
## SYNOPSIS
Retrieve general settings for a Falcon Firewall Management policy
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
## SYNTAX
```powershell
Get-FalconFirewallSetting [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fwmgr/entities/policies/v1
```
### falconpy
[get_policy_containers](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#get_policy_containers)
## USAGE
### View policy settings
```powershell
Get-FalconFirewallSetting -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
