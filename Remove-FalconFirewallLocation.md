# Remove-FalconFirewallLocation
## SYNOPSIS
Remove Falcon Firewall Management locations
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Location identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFirewallLocation [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /fwmgr/entities/network-locations/v1
```
### falconpy
[delete_network_locations](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#delete_network_locations)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
