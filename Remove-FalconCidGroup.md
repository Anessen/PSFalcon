# Remove-FalconCidGroup
## SYNOPSIS
Remove Falcon Flight Control CID groups
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|CID group||||X|X|
## SYNTAX
```powershell
Remove-FalconCidGroup [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /mssp/entities/cid-groups/v1
```
### falconpy
[deleteCIDGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#deleteCIDGroups)
## USAGE
### Delete a CID group
```powershell
Remove-FalconCidGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
