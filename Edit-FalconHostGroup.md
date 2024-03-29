# Edit-FalconHostGroup
## SYNOPSIS
Modify a host group
## DESCRIPTION
Requires 'Host groups: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Host group name|||||X|
|Description|String|Host group description|||||X|
|AssignmentRule|String|FQL-based assignment rule, used with dynamic host groups|||||X|
|Id|String|Host group identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconHostGroup [[-Name] <String>] [[-Description] <String>] [[-AssignmentRule] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /devices/entities/host-groups/v1
```
### falconpy
[updateHostGroups](https://github.com/CrowdStrike/falconpy/wiki/host-group#updateHostGroups)
## USAGE
### Modifying host group details
```powershell
Edit-FalconHostGroup -Id <id> -Name 'Example group 1'
```

_2023-11-27: PSFalcon v2.2.6_
