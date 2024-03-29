# Get-FalconMemberCid
## SYNOPSIS
Search for Falcon Flight Control member CIDs
## DESCRIPTION
Requires 'Flight Control: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Member CID identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`last_modified_timestamp.asc`<BR>`last_modified_timestamp.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconMemberCid [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconMemberCid -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /mssp/queries/children/v1
POST /mssp/entities/children/GET/v2
```
### falconpy
[queryChildren](https://github.com/CrowdStrike/falconpy/wiki/mssp#queryChildren)<BR>[getChildrenV2](https://github.com/CrowdStrike/falconpy/wiki/mssp#getChildrenV2)
## USAGE
### List member CIDs
```powershell
Get-FalconMemberCid [-Detailed] [-All]
```
_See [Authorize and run commands in member CIDs](code-examples#authorize-and-run-commands-in-member-cids)._

_2023-11-27: PSFalcon v2.2.6_
