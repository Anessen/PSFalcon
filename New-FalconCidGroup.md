# New-FalconCidGroup
## SYNOPSIS
Create a Falcon Flight Control CID group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|CID group name||||||
|Description|String|CID group description||||||
## SYNTAX
```powershell
New-FalconCidGroup [-Name] <String> [-Description] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /mssp/entities/cid-groups/v1
```
### falconpy
[createCIDGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#createCIDGroups)
## USAGE
### Create a CID group
```powershell
New-FalconCidGroup -Name 'Manual Testing' -Description 'Manual Testing'
```

_2023-04-25: PSFalcon v2.2.5_
