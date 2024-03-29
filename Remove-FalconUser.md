# Remove-FalconUser
## SYNOPSIS
Remove a user
## DESCRIPTION
Requires 'User management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|User identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconUser [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /user-management/entities/users/v1
```
### falconpy
[deleteUserV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#deleteUserV1)
## USAGE
### Remove a user
```powershell
Remove-FalconUser -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
