# Get-FalconFirewallPolicyMember
## SYNOPSIS
Search for Falcon Firewall Management policy members
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Policy identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFirewallPolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallPolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/firewall-members/v1
GET /policy/queries/firewall-members/v1
```
### falconpy
[queryFirewallPolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#queryFirewallPolicyMembers)<BR>[queryCombinedFirewallPolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#queryCombinedFirewallPolicyMembers)
## USAGE
### List IDs of firewall policy members
```powershell
Get-FalconFirewallPolicyMember -Id <id> [-All]
```

_2023-04-25: PSFalcon v2.2.5_
