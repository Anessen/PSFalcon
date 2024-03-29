# New-FalconUser
## SYNOPSIS
Create a user
## DESCRIPTION
Requires 'User management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Username|String|Username||||X|X|
|FirstName|String|First name|||||X|
|LastName|String|Last name|||||X|
|Password|String|Password. If left unspecified, the user will be emailed a|||||X|
|Cid|String|Customer identifier|||||X|
|ValidateOnly|Boolean|Validate if user is allowed but do not create them|||||X|
## SYNTAX
```powershell
New-FalconUser [-Username] <String> [[-FirstName] <String>] [[-LastName] <String>] [[-Password] <String>] [[-Cid] <String>] [[-ValidateOnly] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /user-management/entities/users/v1
```
### falconpy
[createUserV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#createUserV1)
## USAGE
### Create a new user
```powershell
New-FalconUser -Username jane.doe@example.com
```

_2023-04-25: PSFalcon v2.2.5_
