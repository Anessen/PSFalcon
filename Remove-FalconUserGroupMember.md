# Remove-FalconUserGroupMember
## SYNOPSIS
Remove members from a Falcon Flight Control user group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|User group identifier||||||
|UserId|String[]|User identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconUserGroupMember [-Id] <String> [-UserId] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /mssp/entities/user-group-members/v1
```
### falconpy
[deleteUserGroupMembers](https://github.com/CrowdStrike/falconpy/wiki/mssp#deleteUserGroupMembers)
## USAGE
### Remove a user from a user group
```powershell
Remove-FalconUserGroupMember -Id <user_group_id> -UserId <user_id>, <user_id>
```

_2023-04-25: PSFalcon v2.2.5_
