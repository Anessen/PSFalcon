# Get-FalconIoc
## SYNOPSIS
Search for custom indicators
## DESCRIPTION
Requires 'IOC Manager APIs: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Indicator identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`type`<BR>`value`<BR>`action`<BR>`mobile_action`<BR>`severity`<BR>`platforms`<BR>`tags`<BR>`expiration`<BR>`expired`<BR>`applied_globally`<BR>`host_groups`<BR>`created_on`<BR>`created_by`<BR>`modified_on`<BR>`modified_by`<BR>`source`||||||
|Sort|String|Property and direction to sort results|||`action.asc`<BR>`action.desc`<BR>`applied_globally.asc`<BR>`applied_globally.desc`<BR>`metadata.av_hits.asc`<BR>`metadata.av_hits.desc`<BR>`metadata.company_name.raw.asc`<BR>`metadata.company_name.raw.desc`<BR>`created_by.asc`<BR>`created_by.desc`<BR>`created_on.asc`<BR>`created_on.desc`<BR>`expiration.asc`<BR>`expiration.desc`<BR>`expired.asc`<BR>`expired.desc`<BR>`metadata.filename.raw.asc`<BR>`metadata.filename.raw.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`modified_on.asc`<BR>`modified_on.desc`<BR>`metadata.original_filename.raw.asc`<BR>`metadata.original_filename.raw.desc`<BR>`metadata.product_name.raw.asc`<BR>`metadata.product_name.raw.desc`<BR>`metadata.product_version.asc`<BR>`metadata.product_version.desc`<BR>`severity_number.asc`<BR>`severity_number.desc`<BR>`source.asc`<BR>`source.desc`<BR>`type.asc`<BR>`type.desc`<BR>`value.asc`<BR>`value.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`2000`||||
|FromParent|Boolean|Inheritance from parent CID||||||
|Offset|Int32|Position to begin retrieving results||||||
|After|String|Pagination token to retrieve the next set of results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIoc [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-After <String>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoc -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoc [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-FromParent] <Boolean>] [-Offset <Int32>] [-After <String>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /iocs/combined/indicator/v1
GET /iocs/entities/indicators/v1
GET /iocs/queries/indicators/v1
```
### falconpy
[indicator_search_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#indicator_search_v1)<BR>[indicator_get_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#indicator_get_v1)<BR>[indicator_combined_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#indicator_combined_v1)
## USAGE
### Finding domain indicator identifiers
```powershell
Get-FalconIoc -Filter "type:'domain'
```
### Retrieving details about an indicator by its identifier
```powershell
Get-FalconIoc -Id <id>, <id>
```
### Retrieving indicator details in large batches
```powershell
Get-FalconIoc -Filter "type:'domain'+tags:'MalDomain_20201215'+tags:'domains_mac'" -Detailed -All
```
_See [Get-FalconIocHost](Get-FalconIocHost)_.  _See [Get-FalconIocProcess](Get-FalconIocProcess)_.

_2023-04-25: PSFalcon v2.2.5_
