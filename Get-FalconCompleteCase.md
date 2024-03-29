# Get-FalconCompleteCase
## SYNOPSIS
Search for Falcon Complete cases
## DESCRIPTION
Requires 'Message Center: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Case identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`case.created_time.asc`<BR>`case.created_time.desc`<BR>`case.id.asc`<BR>`case.id.desc`<BR>`case.last_modified_time.asc`<BR>`case.last_modified_time.desc`<BR>`case.status.asc`<BR>`case.status.desc`<BR>`case.type.asc`<BR>`case.type.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|String|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconCompleteCase [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconCompleteCase -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /message-center/queries/cases/v1
POST /message-center/entities/cases/GET/v1
```
### falconpy
[QueryCasesIdsByFilter](https://github.com/CrowdStrike/falconpy/wiki/message-center#QueryCasesIdsByFilter)<BR>[GetCaseEntitiesByIDs](https://github.com/CrowdStrike/falconpy/wiki/message-center#GetCaseEntitiesByIDs)
## USAGE
### Getting a list of case IDs
```powershell
Get-FalconCompleteCase -Limit 10 -Sort case.id.desc
```
### Viewing the details of multiple cases
```powershell
Get-FalconCompleteCase -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
