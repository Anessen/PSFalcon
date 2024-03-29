# Add-FalconCidGroupMember
## SYNOPSIS
Add a CID member to a Falcon Flight Control CID group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|CID group identifier|||||X|
|Cid|String[]|Customer identifier|||||X|
## SYNTAX
```powershell
Add-FalconCidGroupMember [-Id] <String> [-Cid] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /mssp/entities/cid-group-members/v1
```
### falconpy
[addCIDGroupMembers](https://github.com/CrowdStrike/falconpy/wiki/mssp#addCIDGroupMembers)
## USAGE
### Add a CID to a CID group
```powershell
Add-FalconCidGroupMember -Id <cid_group_id> -Cid <cid>, <cid>
```

_2023-04-25: PSFalcon v2.2.5_
