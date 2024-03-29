# Get-FalconHostGroup
## SYNOPSIS
Search for host groups
## DESCRIPTION
Requires 'Host groups: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Host group identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`created_by.asc`<BR>`created_by.desc`<BR>`created_timestamp.asc`<BR>`created_timestamp.desc`<BR>`group_type.asc`<BR>`group_type.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Include|String[]|Include additional properties|||`members`|||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHostGroup [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHostGroup -Id <String[]> [[-Include] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHostGroup [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /devices/combined/host-groups/v1
GET /devices/entities/host-groups/v1
GET /devices/queries/host-groups/v1
```
### falconpy
[queryHostGroups](https://github.com/CrowdStrike/falconpy/wiki/host-group#queryHostGroups)<BR>[getHostGroups](https://github.com/CrowdStrike/falconpy/wiki/host-group#getHostGroups)<BR>[queryCombinedHostGroups](https://github.com/CrowdStrike/falconpy/wiki/host-group#queryCombinedHostGroups)
## USAGE
### Retrieving host group IDs with a filter
```powershell
Get-FalconHostGroup -Filter "group_type:'static'" [-All]
```
### Retrieving host group IDs with a limit
```powershell
Get-FalconHostGroup -Limit 10
```
### Getting details of multiple host groups by ID
```powershell
Get-FalconHostGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
