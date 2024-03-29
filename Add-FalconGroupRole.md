# Add-FalconGroupRole
## SYNOPSIS
Assign roles between Falcon Flight Control CID and user groups
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|CidGroupId|String|CID group identifier|||||X|
|UserGroupId|String|User Group identifier|||||X|
|RoleId|String[]|Role identifier|||||X|
## SYNTAX
```powershell
Add-FalconGroupRole [-CidGroupId] <String> [-UserGroupId] <String> [-RoleId] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /mssp/entities/mssp-roles/v1
```
### falconpy
[addRole](https://github.com/CrowdStrike/falconpy/wiki/mssp#addRole)
## USAGE
### Create a role assignment
```powershell
Add-FalconGroupRole -CidGroupId <cid_group_id> -UserGroupId <user_group_id> -RoleId <role_id>, <role_id>
```

_2023-04-25: PSFalcon v2.2.5_
