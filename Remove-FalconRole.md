# Remove-FalconRole
## SYNOPSIS
Remove roles from a user
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
Remove-FalconRole [-UserId] <String> [-Cid] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /user-management/entities/user-role-actions/v1
```
### falconpy
[userRolesActionV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#userRolesActionV1)
## USAGE
### Revoke roles from a user
*NOTE*: Custom roles are not able to be removed through the CrowdStrike APIs.
```powershell
Remove-FalconRole -Id <id>, <id> -UserId <id> -Cid <cid>
```

_2023-10-13: PSFalcon v2.2.5_
