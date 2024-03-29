# Edit-FalconUserGroup
## SYNOPSIS
Modify a Falcon Flight Control user group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|User group name|||||X|
|Description|String|User group description|||||X|
|Id|String|User group identifier|||||X|
## SYNTAX
```powershell
Edit-FalconUserGroup [[-Name] <String>] [[-Description] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /mssp/entities/user-groups/v1
```
### falconpy
[updateUserGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#updateUserGroups)
## USAGE
### Update a user group
```powershell
Edit-FalconUserGroup -Id <id> -Name 'Updated Name' -Description 'Updated name for manual testing'
```

_2023-04-25: PSFalcon v2.2.5_
