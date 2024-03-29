# Remove-FalconHostGroup
## SYNOPSIS
Remove host groups
## DESCRIPTION
Requires 'Host groups: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Host group identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconHostGroup [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /devices/entities/host-groups/v1
```
### falconpy
[deleteHostGroups](https://github.com/CrowdStrike/falconpy/wiki/host-group#deleteHostGroups)
## USAGE
### Deleting host groups
```powershell
Remove-FalconHostGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
