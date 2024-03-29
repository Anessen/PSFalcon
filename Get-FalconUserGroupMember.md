# Get-FalconUserGroupMember
## SYNOPSIS
Search for members of a Falcon Flight Control user group,or groups assigned to a user
## DESCRIPTION
Requires 'Flight Control: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|User group identifier, to find group members||||X|X|
|UserId|String|A user identifier, to find group membership|||||X|
|Sort|String|Property and direction to sort results|||`last_modified_timestamp.asc`<BR>`last_modified_timestamp.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconUserGroupMember [-UserId] <String> [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconUserGroupMember -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /mssp/entities/user-group-members/v2
GET /mssp/queries/user-group-members/v1
```
### falconpy
[queryUserGroupMembers](https://github.com/CrowdStrike/falconpy/wiki/mssp#queryUserGroupMembers)<BR>[getUserGroupMembersByIDV2](https://github.com/CrowdStrike/falconpy/wiki/mssp#getUserGroupMembersByIDV2)
## USAGE
### List the groups that a user belongs to
```powershell
Get-FalconUserGroupMember -UserId <user_id>
```
### List members of a user group
```powershell
Get-FalconUserGroupMember -Id <user_group_id>
```

_2023-04-25: PSFalcon v2.2.5_
