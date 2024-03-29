# Get-FalconCve
## SYNOPSIS
Search for Falcon Intelligence CVE reports
## DESCRIPTION
Requires 'Vulnerabilities (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|CVE identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|String|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconCve [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconCve -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/queries/vulnerabilities/v1
POST /intel/entities/vulnerabilities/GET/v1
```
### falconpy
[QueryVulnerabilities](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryVulnerabilities)<BR>[GetVulnerabilities](https://github.com/CrowdStrike/falconpy/wiki/intel#GetVulnerabilities)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
