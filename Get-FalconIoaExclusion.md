# Get-FalconIoaExclusion
## SYNOPSIS
Search for Indicator of Attack exclusions
## DESCRIPTION
Requires 'IOA Exclusions: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Exclusion identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`applied_globally.asc`<BR>`applied_globally.desc`<BR>`created_by.asc`<BR>`created_by.desc`<BR>`created_on.asc`<BR>`created_on.desc`<BR>`last_modified.asc`<BR>`last_modified.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`name.asc`<BR>`name.desc`<BR>`pattern_id.asc`<BR>`pattern_id.desc`<BR>`pattern_name.asc`<BR>`pattern_name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIoaExclusion [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoaExclusion -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/entities/ioa-exclusions/v1
GET /policy/queries/ioa-exclusions/v1
```
### falconpy
[queryIOAExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ioa-exclusions#queryIOAExclusionsV1)<BR>[getIOAExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ioa-exclusions#getIOAExclusionsV1)
## USAGE
### Find IOA exclusions
```powershell
Get-FalconIoaExclusion [-Detailed]
```

_2023-04-25: PSFalcon v2.2.5_
