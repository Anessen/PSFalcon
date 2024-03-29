# Get-FalconRole
## SYNOPSIS
Search for user roles and assignments
## DESCRIPTION
Requires 'User management: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Role identifier||||X|X|
|UserId|String|User identifier||||||
|Cid|String|Customer identifier||||||
|DirectOnly|Boolean|Display direct user role grants||||||
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`role_name`<BR>`role_id`||||||
|Sort|String|Property and direction to sort results|||`cid\|asc`<BR>`cid\|desc`<BR>`role_name\|asc`<BR>`role_name\|desc`<BR>`type\|asc`<BR>`type\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|String|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconRole [-Cid <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconRole -Id <String[]> [[-Cid] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconRole -UserId <String> [[-Cid] <String>] [[-DirectOnly] <Boolean>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /user-management/combined/user-roles/v1
GET /user-management/entities/roles/v1
GET /user-management/queries/roles/v1
```
### falconpy
[queriesRolesV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#queriesRolesV1)<BR>[entitiesRolesV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#entitiesRolesV1)<BR>[combinedUserRolesV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#combinedUserRolesV1)
## USAGE
### List all available user roles
```powershell
Get-FalconRole [-Detailed]
```
### List roles assigned to a user
```powershell
Get-FalconRole -UserId <id>
```

_2023-11-27: PSFalcon v2.2.6_
