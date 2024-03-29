# Get-FalconIoaSeverity
## SYNOPSIS
Search for custom Indicator of Attack severity levels
## DESCRIPTION
Requires 'Custom IOA rules: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Severity identifier|||`critical`<BR>`high`<BR>`medium`<BR>`low`<BR>`informational`|X|X|
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIoaSeverity [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoaSeverity -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ioarules/entities/pattern-severities/v1
GET /ioarules/queries/pattern-severities/v1
```
### falconpy
[query_patterns](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#query_patterns)<BR>[get_patterns](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#get_patterns)
## USAGE
### Find custom IOA severities
```powershell
Get-FalconIoaSeverity [-Detailed]
```

_2023-04-25: PSFalcon v2.2.5_
