# Set-FalconFirewallLocationPrecedence
## SYNOPSIS
Set Falcon Firewall Management location precedence
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Cid|String|Customer identifier||||||
|Comment|String|Audit log comment||||||
|Id|String[]|Location identifiers in desired precedence order||||||
## SYNTAX
```powershell
Set-FalconFirewallLocationPrecedence [[-Cid] <String>] [[-Comment] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /fwmgr/entities/network-locations-precedence/v1
```
### falconpy
[update_network_locations_precedence](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#update_network_locations_precedence)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
