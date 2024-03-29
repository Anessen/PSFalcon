# Remove-FalconGroupRole
## SYNOPSIS
Remove roles between a Falcon Flight Control user group and CID group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|CidGroupId|String|CID group identifier|||||X|
|UserGroupId|String|User group identifier|||||X|
|RoleId|String[]|Role identifier, or leave blank to remove user group/CID group association|||||X|
## SYNTAX
```powershell
Remove-FalconGroupRole [-CidGroupId] <String> [-UserGroupId] <String> [[-RoleId] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /mssp/entities/mssp-roles/v1
```
### falconpy
[deletedRoles](https://github.com/CrowdStrike/falconpy/wiki/mssp#deletedRoles)
## USAGE
### Delete a role assignment
```powershell
Remove-FalconGroupRole -CidGroupId <cid_group_id> -UserGroupId <user_group_id> -RoleId <role_id>, <role_id>
```

_2023-04-25: PSFalcon v2.2.5_
