# Edit-FalconUser
## SYNOPSIS
Modify the name of a user
## DESCRIPTION
Requires 'User management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|FirstName|String|First name||||||
|LastName|String|Last name||||||
|Id|String|User identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconUser [[-FirstName] <String>] [[-LastName] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /user-management/entities/users/v1
```
### falconpy
[updateUserV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#updateUserV1)
## USAGE
### Modify the first and last name of a user
```powershell
Edit-FalconUser -Id <id> -FirstName Jane -LastName Doe
```

_2023-04-25: PSFalcon v2.2.5_
