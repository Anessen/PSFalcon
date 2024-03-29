# Get-FalconCompleteActivity
## SYNOPSIS
Search for Falcon Complete case activities
## DESCRIPTION
Requires 'Message Center: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Activity identifier||||X|X|
|CaseId|String|Case identifier||||||
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`activity.created_time.asc`<BR>`activity.created_time.desc`<BR>`activity.type.asc`<BR>`activity.type.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|String|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconCompleteActivity [-CaseId] <String> [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconCompleteActivity -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /message-center/queries/case-activities/v1
POST /message-center/entities/case-activities/GET/v1
```
### falconpy
[QueryActivityByCaseID](https://github.com/CrowdStrike/falconpy/wiki/message-center#QueryActivityByCaseID)<BR>[GetCaseActivityByIds](https://github.com/CrowdStrike/falconpy/wiki/message-center#GetCaseActivityByIds)
## USAGE
### Getting a list of activity IDs
```powershell
Get-FalconCompleteActivity -CaseId <id>
```
### Viewing the messages and status changes of a case
```powershell
Get-FalconCompleteActivity -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
