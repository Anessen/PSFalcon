# Get-FalconIntel
## SYNOPSIS
Search for intelligence reports
## DESCRIPTION
Requires 'Reports (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Report identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`actors`<BR>`actors.name`<BR>`created_date`<BR>`description`<BR>`id`<BR>`last_modified_date`<BR>`motivations`<BR>`motivations.value`<BR>`name`<BR>`short_description`<BR>`sub_type`<BR>`sub_type.value`<BR>`tags`<BR>`tags.value`<BR>`target_countries`<BR>`target_countries.value`<BR>`target_industries`<BR>`target_industries.value`<BR>`type`<BR>`type.value`||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`name\|asc`<BR>`name\|desc`<BR>`target_countries\|asc`<BR>`target_countries\|desc`<BR>`target_industries\|asc`<BR>`target_industries\|desc`<BR>`type\|asc`<BR>`type\|desc`<BR>`created_date\|asc`<BR>`created_date\|desc`<BR>`last_modified_date\|asc`<BR>`last_modified_date\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Field|String[]|Specific fields, or a predefined collection name surrounded by two underscores [default: __basic__]||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIntel [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIntel -Id <String[]> [[-Field] <String[]>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIntel [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Field] <String[]>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/combined/reports/v1
GET /intel/entities/reports/v1
GET /intel/queries/reports/v1
```
### falconpy
[QueryIntelReportIds](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryIntelReportIds)<BR>[GetIntelReportEntities](https://github.com/CrowdStrike/falconpy/wiki/intel#GetIntelReportEntities)<BR>[QueryIntelReportEntities](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryIntelReportEntities)
## USAGE
### Search for report IDs by criteria
```powershell
Get-FalconIntel -Filter "target_countries:'united states'+target_industries:'government'"
```
### Search for reports using a specific ID
```powershell
Get-FalconIntel -Id <id>, <id>
```
### Search for detailed report information
```powershell
Get-FalconIntel -Filter "target_countries:'afghanistan'" -Limit 1 -Detailed
```

_2023-04-25: PSFalcon v2.2.5_
