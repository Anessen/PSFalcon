# Get-FalconScan
## SYNOPSIS
Search for on-demand or scheduled scan results
## DESCRIPTION
Requires 'On-demand scans (ODS): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Scan result identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`id\|asc`<BR>`id\|desc`<BR>`initiated_from\|asc`<BR>`initiated_from\|desc`<BR>`description.keyword\|asc`<BR>`description.keyword\|desc`<BR>`filecount.scanned\|asc`<BR>`filecount.scanned\|desc`<BR>`filecount.malicious\|asc`<BR>`filecount.malicious\|desc`<BR>`filecount.quarantined\|asc`<BR>`filecount.quarantined\|desc`<BR>`filecount.skipped\|asc`<BR>`filecount.skipped\|desc`<BR>`affected_hosts_count\|asc`<BR>`affected_hosts_count\|desc`<BR>`status\|asc`<BR>`status\|desc`<BR>`severity\|asc`<BR>`severity\|desc`<BR>`scan_started_on\|asc`<BR>`scan_started_on\|desc`<BR>`scan_completed_on\|asc`<BR>`scan_completed_on\|desc`<BR>`created_on\|asc`<BR>`created_on\|desc`<BR>`created_by\|asc`<BR>`created_by\|desc`<BR>`last_updated\|asc`<BR>`last_updated\|desc`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconScan [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScan -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ods/entities/scans/v2
GET /ods/queries/scans/v1
```
### falconpy
[query_scans](https://github.com/CrowdStrike/falconpy/wiki/ods#query_scans)<BR>[get_scans_by_scan_ids_v2](https://github.com/CrowdStrike/falconpy/wiki/ods#get_scans_by_scan_ids_v2)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
