# Invoke-FalconUserAction
## SYNOPSIS
Perform an action on a user
## DESCRIPTION
Requires 'User management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action name|||`reset_password`<BR>`reset_2fa`|||
|Id|String[]|User identifier||||||
## SYNTAX
```powershell
Invoke-FalconUserAction [-Name] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /user-management/entities/user-actions/v1
```
### falconpy
[userActionV1](https://github.com/CrowdStrike/falconpy/wiki/user-management#userActionV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
