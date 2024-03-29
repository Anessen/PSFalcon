# Get-FalconScanFile
## SYNOPSIS
Search for files found by on-demand or scheduled scans
## DESCRIPTION
Requires 'On-demand scans (ODS): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Malicious file identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`id\|asc`<BR>`id\|desc`<BR>`scan_id\|asc`<BR>`scan_id\|desc`<BR>`host_id\|asc`<BR>`host_id\|desc`<BR>`host_scan_id\|asc`<BR>`host_scan_id\|desc`<BR>`filename\|asc`<BR>`filename\|desc`<BR>`hash\|asc`<BR>`hash\|desc`<BR>`pattern_id\|asc`<BR>`pattern_id\|desc`<BR>`severity\|asc`<BR>`severity\|desc`<BR>`last_updated\|asc`<BR>`last_updated\|desc`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconScanFile [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconScanFile -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ods/entities/malicious-files/v1
GET /ods/queries/malicious-files/v1
```
### falconpy
[query_malicious_files](https://github.com/CrowdStrike/falconpy/wiki/ods#query_malicious_files)<BR>[get_malicious_files_by_ids](https://github.com/CrowdStrike/falconpy/wiki/ods#get_malicious_files_by_ids)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
