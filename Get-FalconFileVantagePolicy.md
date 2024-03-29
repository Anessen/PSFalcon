# Get-FalconFileVantagePolicy
## SYNOPSIS
Search for FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|FileVantage policy identifier||||X|X|
|Type|String|Operating system type|||`Linux`<BR>`Mac`<BR>`Windows`|||
|Sort|String|Property and direction to sort results|||`created_timestamp\|asc`<BR>`created_timestamp\|desc`<BR>`modified_timestamp\|asc`<BR>`modified_timestamp\|desc`<BR>`precedence\|asc`<BR>`precedence\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Include|String[]|Include additional properties|||`exclusions`|||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFileVantagePolicy [-Type] <String> [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFileVantagePolicy -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /filevantage/entities/policies/v1
GET /filevantage/queries/policies/v1
```
### falconpy
[queryPolicies](https://github.com/CrowdStrike/falconpy/wiki/filevantage#queryPolicies)<BR>[getPolicies](https://github.com/CrowdStrike/falconpy/wiki/filevantage#getPolicies)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
