# Get-FalconScanHost
## SYNOPSIS
Search for on-demand or scheduled scan metadata for specific hosts
## DESCRIPTION
Requires 'On-demand scans (ODS): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|Object[]|Scanned host metadata identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`id\|asc`<BR>`id\|desc`<BR>`scan_id\|asc`<BR>`scan_id\|desc`<BR>`host_id\|asc`<BR>`host_id\|desc`<BR>`filecount.scanned\|asc`<BR>`filecount.scanned\|desc`<BR>`filecount.malicious\|asc`<BR>`filecount.malicious\|desc`<BR>`filecount.quarantined\|asc`<BR>`filecount.quarantined\|desc`<BR>`filecount.skipped\|asc`<BR>`filecount.skipped\|desc`<BR>`status\|asc`<BR>`status\|desc`<BR>`severity\|asc`<BR>`severity\|desc`<BR>`started_on\|asc`<BR>`started_on\|desc`<BR>`completed_on\|asc`<BR>`completed_on\|desc`<BR>`last_updated\|asc`<BR>`last_updated\|desc`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconScanHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScanHost -Id <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ods/entities/scan-hosts/v1
GET /ods/queries/scan-hosts/v1
```
### falconpy
[query_scan_host_metadata](https://github.com/CrowdStrike/falconpy/wiki/ods#query_scan_host_metadata)<BR>[get_scan_host_metadata_by_ids](https://github.com/CrowdStrike/falconpy/wiki/ods#get_scan_host_metadata_by_ids)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
