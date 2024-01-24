# Get-FalconFileVantageChange
## SYNOPSIS
Search for Falcon FileVantage changes
## DESCRIPTION
Requires 'Falcon FileVantage: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|FileVantage change identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`action_timestamp`<BR>`ingestion_timestamp`<BR>`host.name`<BR>`severity`||||||
|Sort|String|Property and direction to sort results|||`action_timestamp\|asc`<BR>`action_timestamp\|desc`<BR>`ingestion_timestamp\|asc`<BR>`ingestion_timestamp\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|After|String|Pagination token to retrieve the next set of results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFileVantageChange [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-After <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFileVantageChange -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /filevantage/entities/changes/v2
GET /filevantage/queries/changes/v3
```
### falconpy
[highVolumeQueryChanges](https://github.com/CrowdStrike/falconpy/wiki/filevantage#highVolumeQueryChanges)<BR>[getChanges](https://github.com/CrowdStrike/falconpy/wiki/filevantage#getChanges)
## USAGE

_2024-01-24: PSFalcon v2.2.6_
