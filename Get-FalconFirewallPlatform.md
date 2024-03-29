# Get-FalconFirewallPlatform
## SYNOPSIS
Search for Falcon Firewall Management platforms
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Platform identifier|||`0`<BR>`1`|X|X|
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFirewallPlatform [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallPlatform -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fwmgr/entities/platforms/v1
GET /fwmgr/queries/platforms/v1
```
### falconpy
[query_platforms](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#query_platforms)<BR>[get_platforms](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#get_platforms)
## USAGE
### List available firewall platforms
```powershell
Get-FalconFirewallPlatform -Detailed
```

_2023-04-25: PSFalcon v2.2.5_
