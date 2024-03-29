# Get-FalconFirewallEvent
## SYNOPSIS
Search for Falcon Firewall Management events
## DESCRIPTION
Requires 'Firewall management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Event identifier||||X|X|
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
Get-FalconFirewallEvent [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-After <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFirewallEvent -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /fwmgr/entities/events/v1
GET /fwmgr/queries/events/v1
```
### falconpy
[query_events](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#query_events)<BR>[get_events](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#get_events)
## USAGE
### List firewall rule events
```powershell
Get-FalconFirewallEvent [-Detailed] [-All]
```
### Find information about an event
```powershell
Get-FalconFirewallEvent -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
