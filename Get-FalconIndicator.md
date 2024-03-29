# Get-FalconIndicator
## SYNOPSIS
Search for intelligence indicators
## DESCRIPTION
Requires 'Indicators (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Indicator identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`actors`<BR>`deleted`<BR>`domain_types`<BR>`id`<BR>`indicator`<BR>`ip_address_types`<BR>`kill_chains`<BR>`labels`<BR>`labels.name`<BR>`last_updated`<BR>`malicious_confidence`<BR>`malware_families`<BR>`published_date`<BR>`reports`<BR>`targets`<BR>`threat_types`<BR>`type`<BR>`vulnerabilities`||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`id\|asc`<BR>`id\|desc`<BR>`indicator\|asc`<BR>`indicator\|desc`<BR>`type\|asc`<BR>`type\|desc`<BR>`published_date\|asc`<BR>`published_date\|desc`<BR>`last_updated\|asc`<BR>`last_updated\|desc`<BR>`_marker\|asc`<BR>`_marker\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|IncludeDeleted|Boolean|Include previously deleted indicators||||||
|IncludeRelation|Boolean|Include related indicators||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIndicator [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-IncludeDeleted] <Boolean>] [[-IncludeRelation] <Boolean>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIndicator -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIndicator [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-IncludeDeleted] <Boolean>] [[-IncludeRelation] <Boolean>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/combined/indicators/v1
GET /intel/queries/indicators/v1
POST /intel/entities/indicators/GET/v1
```
### falconpy
[QueryIntelIndicatorIds](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryIntelIndicatorIds)<BR>[GetIntelIndicatorEntities](https://github.com/CrowdStrike/falconpy/wiki/intel#GetIntelIndicatorEntities)<BR>[QueryIntelIndicatorEntities](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryIntelIndicatorEntities)
## USAGE
### Search for indicator IDs
```powershell
Get-FalconIndicator -Filter "type:'domain'" [-All]
```
### Get indicators by ID
```powershell
Get-FalconIndicator -Id <id>, <id>
```
### Search for detailed indicator information
```powershell
Get-FalconIndicator -Filter "last_updated:>=1427846400" -Sort "last_updated|asc" -Detailed [-All]
```

_2023-04-25: PSFalcon v2.2.5_
