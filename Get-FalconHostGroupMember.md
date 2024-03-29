# Get-FalconHostGroupMember
## SYNOPSIS
Search for host group members
## DESCRIPTION
Requires 'Host groups: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Host group identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|The maximum records to return|`1`|`500`||||
|Offset|Int32|The offset to start retrieving records from||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHostGroupMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHostGroupMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /devices/combined/host-group-members/v1
GET /devices/queries/host-group-members/v1
```
### falconpy
[queryGroupMembers](https://github.com/CrowdStrike/falconpy/wiki/host-group#queryGroupMembers)<BR>[queryCombinedGroupMembers](https://github.com/CrowdStrike/falconpy/wiki/host-group#queryCombinedGroupMembers)
## USAGE
### Retrieving the IDs of the first 5 hosts in a host group
```powershell
Get-FalconHostGroupMember -Id <id> -Limit 5
```
### Retrieving the details of hosts in a host group
```powershell
Get-FalconHostGroupMember -Id <id> -Detailed
```

_2023-04-25: PSFalcon v2.2.5_
