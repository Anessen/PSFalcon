# Get-FalconReconRule
## SYNOPSIS
Search for Falcon Intelligence Recon monitoring rules
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Monitoring rule identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`created_timestamp\|asc`<BR>`created_timestamp\|desc`<BR>`last_updated_timestamp\|asc`<BR>`last_updated_timestamp\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconReconRule [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReconRule -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /recon/entities/rules/v1
GET /recon/queries/rules/v1
```
### falconpy
[QueryRulesV1](https://github.com/CrowdStrike/falconpy/wiki/recon#QueryRulesV1)<BR>[GetRulesV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetRulesV1)
## USAGE
### Finding a monitoring rule
```powershell
Get-FalconReconRule [-Detailed]
```

_2023-04-25: PSFalcon v2.2.5_
