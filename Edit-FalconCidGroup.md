# Edit-FalconCidGroup
## SYNOPSIS
Modify a Falcon Flight Control CID group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|CID group name|||||X|
|Description|String|CID group description|||||X|
|Id|String|CID group identifier|||||X|
## SYNTAX
```powershell
Edit-FalconCidGroup [[-Name] <String>] [[-Description] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /mssp/entities/cid-groups/v1
```
### falconpy
[updateCIDGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#updateCIDGroups)
## USAGE
### Update a CID group
```powershell
Edit-FalconCidGroup -Id <id> -Name 'Updated Name' -Description 'Updated name for manual testing'
```

_2023-04-25: PSFalcon v2.2.5_
