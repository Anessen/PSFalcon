# Remove-FalconUserGroup
## SYNOPSIS
Remove Falcon Flight Control user groups
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|User group identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconUserGroup [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /mssp/entities/user-groups/v1
```
### falconpy
[deleteUserGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#deleteUserGroups)
## USAGE
### Delete a user group
```powershell
Remove-FalconUserGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
