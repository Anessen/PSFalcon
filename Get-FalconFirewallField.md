# Get-FalconFirewallField
## SYNOPSIS
Search for Falcon Firewall Management fields
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Field identifier||||X|X|
|PlatformId|String|Operating System platform|||`0`<BR>`1`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFirewallField [[-PlatformId] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallField -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fwmgr/entities/firewall-fields/v1
GET /fwmgr/queries/firewall-fields/v1
```
### falconpy
[query_firewall_fields](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#query_firewall_fields)<BR>[get_firewall_fields](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#get_firewall_fields)
## USAGE
### List available firewall fields
```powershell
Get-FalconFirewallField -Detailed
```

_2023-04-25: PSFalcon v2.2.5_
