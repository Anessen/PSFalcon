# Get-FalconFirewallLocation
## SYNOPSIS
Search for Falcon Firewall Management locations
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Location identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|String|Position to begin retrieving results||||||
|After|String|Pagination token to retrieve the next set of results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFirewallLocation [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-After <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallLocation -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fwmgr/entities/network-locations-details/v1
GET /fwmgr/queries/network-locations/v1
```
### falconpy
[query_network_locations](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#query_network_locations)<BR>[get_network_locations_details](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#get_network_locations_details)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
