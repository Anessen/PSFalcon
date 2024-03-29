# Add-FalconRole
## SYNOPSIS
Assign roles to users
## DESCRIPTION
Requires 'User management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|UserId|String|User identifier|||||X|
|Cid|String|Customer identifier|||||X|
|Id|String[]|User role||||||
## SYNTAX
```powershell
Add-FalconRole [-UserId] <String> [-Cid] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /user-management/entities/user-role-actions/v1
```
### falconpy
[userRolesActionV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#userRolesActionV1)
## USAGE
### Assign roles to a user
*NOTE*: Custom roles are not able to be assigned through the CrowdStrike APIs.
```powershell
Add-FalconRole -Id <id>, <id> -UserId <id> -Cid <cid>
```

_2023-10-13: PSFalcon v2.2.5_
