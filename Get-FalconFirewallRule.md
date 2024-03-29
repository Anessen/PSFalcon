# Get-FalconFirewallRule
## SYNOPSIS
Search for Falcon Firewall Management rules
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Rule identifier||||X|X|
|PolicyId|String|Return rules in precedence order for a specific policy||||||
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|After|String|Pagination token to retrieve the next set of results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFirewallRule [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-After <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallRule -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallRule [-PolicyId] <String> [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fwmgr/entities/rules/v1
GET /fwmgr/queries/policy-rules/v1
GET /fwmgr/queries/rules/v1
```
### falconpy
[query_rules](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#query_rules)<BR>[get_rules](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#get_rules)<BR>[query_policy_rules](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#query_policy_rules)
## USAGE
### Finding information about firewall rules
```powershell
Get-FalconFirewallRule -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
