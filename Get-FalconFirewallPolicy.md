# Get-FalconFirewallPolicy
## SYNOPSIS
Search for Falcon Firewall Management policies
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`created_by.asc`<BR>`created_by.desc`<BR>`created_timestamp.asc`<BR>`created_timestamp.desc`<BR>`enabled.asc`<BR>`enabled.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`<BR>`platform_name.asc`<BR>`platform_name.desc`<BR>`precedence.asc`<BR>`precedence.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Include|String[]|Include additional properties|||`members`<BR>`settings`|||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFirewallPolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallPolicy -Id <String[]> [[-Include] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallPolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/firewall/v1
GET /policy/entities/firewall/v1
GET /policy/queries/firewall/v1
```
### falconpy
[queryFirewallPolicies](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#queryFirewallPolicies)<BR>[getFirewallPolicies](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#getFirewallPolicies)<BR>[queryCombinedFirewallPolicies](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#queryCombinedFirewallPolicies)
## USAGE
### Find information about a policy
```powershell
Get-FalconFirewallPolicy -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
