# Get-FalconCidGroupMember
## SYNOPSIS
Search for Falcon Flight Control CID group members
## DESCRIPTION
Requires 'Flight Control: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|CID group identifier||||X|X|
|Cid|String|CID|||||X|
|Sort|String|Property and direction to sort results|||`last_modified_timestamp.asc`<BR>`last_modified_timestamp.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconCidGroupMember [-Cid] <String> [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconCidGroupMember -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /mssp/entities/cid-group-members/v2
GET /mssp/queries/cid-group-members/v1
```
### falconpy
[queryCIDGroupMembers](https://github.com/CrowdStrike/falconpy/wiki/mssp#queryCIDGroupMembers)<BR>[getCIDGroupMembersByV2](https://github.com/CrowdStrike/falconpy/wiki/mssp#getCIDGroupMembersByV2)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
