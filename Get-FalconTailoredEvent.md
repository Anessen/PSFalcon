# Get-FalconTailoredEvent
## SYNOPSIS
Search for tailored intelligence events
## DESCRIPTION
Requires 'Tailored Intelligence: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Tailored intelligence event identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|String|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconTailoredEvent [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconTailoredEvent [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ti/events/queries/events/v2
POST /ti/events/entities/events/GET/v2
```
### falconpy
[QueryEvents](https://github.com/CrowdStrike/falconpy/wiki/ti#QueryEvents)<BR>[GetEventsEntities](https://github.com/CrowdStrike/falconpy/wiki/ti#GetEventsEntities)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
