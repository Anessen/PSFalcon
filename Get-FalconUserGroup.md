# Get-FalconUserGroup
## SYNOPSIS
Search for Falcon Flight Control user groups
## DESCRIPTION
Requires 'Flight Control: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|User group identifier||||X|X|
|Name|String|User group name||||||
|Sort|String|Property and direction to sort results|||`last_modified_timestamp.asc`<BR>`last_modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconUserGroup [[-Name] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconUserGroup -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /mssp/entities/user-groups/v2
GET /mssp/queries/user-groups/v1
```
### falconpy
[queryUserGroups](https://github.com/CrowdStrike/falconpy/wiki/mssp#queryUserGroups)<BR>[getUserGroupsByIDV2](https://github.com/CrowdStrike/falconpy/wiki/mssp#getUserGroupsByIDV2)
## USAGE
### List user groups by ID
```powershell
Get-FalconUserGroup [-Detailed] [-All]
```
### Retrieve detail about one or more user groups
```powershell
Get-FalconUserGroup -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
