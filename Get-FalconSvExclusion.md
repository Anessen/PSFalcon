# Get-FalconSvExclusion
## SYNOPSIS
Search for Sensor Visibility exclusions
## DESCRIPTION
Requires 'Sensor Visibility Exclusions: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Exclusion identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`applied_globally.asc`<BR>`applied_globally.desc`<BR>`created_by.asc`<BR>`created_by.desc`<BR>`created_on.asc`<BR>`created_on.desc`<BR>`last_modified.asc`<BR>`last_modified.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`value.asc`<BR>`value.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconSvExclusion [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSvExclusion -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/entities/sv-exclusions/v1
GET /policy/queries/sv-exclusions/v1
```
### falconpy
[querySensorVisibilityExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/sensor-visibility-exclusions#querySensorVisibilityExclusionsV1)<BR>[getSensorVisibilityExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/sensor-visibility-exclusions#getSensorVisibilityExclusionsV1)
## USAGE
### Find Sensor Visibility exclusions
```powershell
Get-FalconSvExclusion [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
