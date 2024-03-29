# Get-FalconGroupRole
## SYNOPSIS
Search for Falcon Flight Control user group roles
## DESCRIPTION
Requires 'Flight Control: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Combined group identifier [<cid_group_id>:<user_group_id>]||||X||
|CidGroupId|String|CID group identifier|||||X|
|UserGroupId|String|User group identifier|||||X|
|RoleId|String|Role group identifier|||||X|
|Sort|String|Property and direction to sort results|||`last_modified_timestamp.asc`<BR>`last_modified_timestamp.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconGroupRole [[-CidGroupId] <String>] [[-UserGroupId] <String>] [[-RoleId] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconGroupRole -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /mssp/entities/mssp-roles/v1
GET /mssp/queries/mssp-roles/v1
```
### falconpy
[queryRoles](https://github.com/CrowdStrike/falconpy/wiki/mssp#queryRoles)<BR>[getRolesByID](https://github.com/CrowdStrike/falconpy/wiki/mssp#getRolesByID)
## USAGE
### Get role assignments
```powershell
Get-FalconGroupRole -Id <cid_group_id>:<user_group_id>, <cid_group_id>:<user_group_id>
```
```powershell
Get-FalconGroupRole -CidGroupId <cid_group_id> -UserGroupId <user_group_id>
```

_2023-04-25: PSFalcon v2.2.5_
