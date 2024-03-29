# Get-FalconUser
## SYNOPSIS
Search for users
## DESCRIPTION
Requires 'User management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|User identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`assigned_cids`<BR>`cid`<BR>`first_name`<BR>`last_name`<BR>`name`<BR>`uid`||||||
|Sort|String|Property and direction to sort results|||`first_name\|asc`<BR>`first_name\|desc`<BR>`last_name\|asc`<BR>`last_name\|desc`<BR>`name\|asc`<BR>`name\|desc`<BR>`uid\|asc`<BR>`uid\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Username|String[]|Username||||||
|Include|String[]|Include additional properties|||`roles`|||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconUser [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Include <String[]>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconUser [-Id] <String[]> [-Include <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconUser -Username <String[]> [-Include <String[]>] [-Detailed] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /user-management/queries/users/v1
POST /user-management/entities/users/GET/v1
```
### falconpy
[queryUserV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#queryUserV1)<BR>[retrieveUsersGETV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#retrieveUsersGETV1)
## USAGE
### List all user IDs
```powershell
Get-FalconUser
```
### Find a user ID by username
```powershell
Get-FalconUser -Username jane.doe@example.com
```
### List all users and their details
```powershell
Get-FalconUser -Detailed
```
**NOTE**: The `Include` parameter can be used to append user roles to `Get-FalconUser` output.
### Get details on one or more users
```powershell
Get-FalconUser -Id <id>, <id>
```

_2023-11-27: PSFalcon v2.2.6_
