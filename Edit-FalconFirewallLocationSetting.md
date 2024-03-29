# Edit-FalconFirewallLocationSetting
## SYNOPSIS
Modify Falcon Firewall Management settings for all locations
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Cid|String|Customer identifier||||||
|IcmpInterval|Int32|Number of seconds between each ICMP request attempt||||||
|DnsInterval|Int32|Number of seconds between each DNS request attempt||||||
|HttpsInterval|Int32|Number of seconds between each HTTPS request attempt||||||
|LocationPrecedence|String[]|Location identifiers in desired precedence order||||||
|Comment|String|Audit log comment||||||
## SYNTAX
```powershell
Edit-FalconFirewallLocationSetting [[-Cid] <String>] [[-IcmpInterval] <Int32>] [[-DnsInterval] <Int32>] [[-HttpsInterval] <Int32>] [[-LocationPrecedence] <String[]>] [[-Comment] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /fwmgr/entities/network-locations-metadata/v1
```
### falconpy
[update_network_locations_metadata](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#update_network_locations_metadata)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
