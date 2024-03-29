# New-FalconFirewallLocation
## SYNOPSIS
Create Falcon Firewall Management locations
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|CloneId|String|Clone an existing location|||||X|
|AddFwRule|Boolean|Include firewall rules from existing location||||||
|Name|String|Location name||||||
|Description|String|Location description||||||
|Enabled|Boolean|Location status||||||
|ConnectionType|Object|Wired or wireless connection types with associated properties||||||
|DefaultGateway|String[]|Default gateway IP address or CIDR block||||||
|DhcpServer|String[]|DHCP server IP address or CIDR block||||||
|DnsServer|String[]|DNS server IP address or CIDR block||||||
|HostAddress|String[]|Host IP address or CIDR block||||||
|DnsResolutionTarget|Object[]|Target IP address or CIDR block, with optional domain name||||||
|HttpsReachableHost|String[]|Target domain name using a trusted certificate||||||
|IcmpRequestTarget|String[]|Pingable IP address or CIDR block||||||
|Comment|String|Audit log comment||||||
## SYNTAX
```powershell
New-FalconFirewallLocation [-Name] <String> [[-Description] <String>] [[-Enabled] <Boolean>] [[-ConnectionType] <Object>] [[-DefaultGateway] <String[]>] [[-DhcpServer] <String[]>] [[-DnsServer] <String[]>] [[-HostAddress] <String[]>] [[-DnsResolutionTarget] <Object[]>] [[-HttpsReachableHost] <String[]>] [[-IcmpRequestTarget] <String[]>] [[-Comment] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconFirewallLocation [-CloneId] <String> [[-AddFwRule] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /fwmgr/entities/network-locations/v1
```
### falconpy
[create_network_locations](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#create_network_locations)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
