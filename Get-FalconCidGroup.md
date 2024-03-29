# Get-FalconCidGroup
## SYNOPSIS
Search for Falcon Flight Control CID groups
## DESCRIPTION
Requires 'Flight Control: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|CID group identifier||||X|X|
|Name|String|CID group name||||||
|Sort|String|Property and direction to sort results|||`last_modified_timestamp.asc`<BR>`last_modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconCidGroup [[-Name] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconCidGroup -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /mssp/entities/cid-groups/v2
GET /mssp/queries/cid-groups/v1
```
### falconpy
[queryCIDGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#queryCIDGroups)<BR>[getCIDGroupByIdV2](https://github.com/CrowdStrike/falconpy/wiki/mssp#getCIDGroupByIdV2)
## USAGE
### List CID groups by ID
```powershell
Get-FalconCidGroup [-Detailed] [-All]
```
### Retrieve detail about one or more CID groups
```powershell
Get-FalconCidGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
