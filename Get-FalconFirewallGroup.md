# Get-FalconFirewallGroup
## SYNOPSIS
Search for Falcon Firewall Management rule groups
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Rule group identifier||||X|X|
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
Get-FalconFirewallGroup [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-After <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallGroup -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fwmgr/entities/rule-groups/v1
GET /fwmgr/queries/rule-groups/v1
```
### falconpy
[query_rule_groups](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#query_rule_groups)<BR>[get_rule_groups](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#get_rule_groups)
## USAGE
### Finding rule IDs in a firewall rule group
```powershell
Get-FalconFirewallGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
