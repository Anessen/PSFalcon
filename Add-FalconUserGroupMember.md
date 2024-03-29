# Add-FalconUserGroupMember
## SYNOPSIS
Add a user to a Falcon Flight Control user group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|User group identifier|||||X|
|UserId|String[]|User identifier|||||X|
## SYNTAX
```powershell
Add-FalconUserGroupMember [-Id] <String> [-UserId] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /mssp/entities/user-group-members/v1
```
### falconpy
[addUserGroupMembers](https://github.com/CrowdStrike/falconpy/wiki/mssp#addUserGroupMembers)
## USAGE
### Add a user to a user group
```powershell
Add-FalconUserGroupMember -Id <user_group_id> -UserId <user_id>, <user_id>
```

_2023-04-25: PSFalcon v2.2.5_
