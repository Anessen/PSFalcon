# Remove-FalconCidGroupMember
## SYNOPSIS
Remove members from a Falcon Flight Control CID group
## DESCRIPTION
Requires 'Flight Control: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|CID group identifier|||||X|
|Cid|String[]|Customer identifier|||||X|
## SYNTAX
```powershell
Remove-FalconCidGroupMember [-Id] <String> [-Cid] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /mssp/entities/cid-group-members/v2
```
### falconpy
[deleteCIDGroupMembersV2](https://github.com/CrowdStrike/falconpy/wiki/mssp#deleteCIDGroupMembersV2)
## USAGE
### Remove a CID from a CID group
```powershell
Remove-FalconCidGroupMember -Id <cid_group_id> -Cid <cid>, <cid>
```

_2023-11-27: PSFalcon v2.2.6_
