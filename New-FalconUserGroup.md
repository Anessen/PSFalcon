# New-FalconUserGroup
## SYNOPSIS
Create a Falcon Flight Control user group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|User group name||||||
|Description|String|User group description||||||
## SYNTAX
```powershell
New-FalconUserGroup [-Name] <String> [-Description] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /mssp/entities/user-groups/v1
```
### falconpy
[createUserGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#createUserGroups)
## USAGE
### Create a user group
```powershell
New-FalconUserGroup -Name 'Manual Testing' -Description 'Manual Testing'
```

_2023-04-25: PSFalcon v2.2.5_
