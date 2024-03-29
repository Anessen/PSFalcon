# Get-FalconPreventionPolicy
## SYNOPSIS
Search for Prevention policies
## DESCRIPTION
Requires 'Prevention Policies: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`created_by.asc`<BR>`created_by.desc`<BR>`created_timestamp.asc`<BR>`created_timestamp.desc`<BR>`enabled.asc`<BR>`enabled.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`<BR>`platform_name.asc`<BR>`platform_name.desc`<BR>`precedence.asc`<BR>`precedence.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Include|String[]|Include additional properties|||`members`|||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconPreventionPolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconPreventionPolicy -Id <String[]> [[-Include] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconPreventionPolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/prevention/v1
GET /policy/entities/prevention/v1
GET /policy/queries/prevention/v1
```
### falconpy
[queryPreventionPolicies](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#queryPreventionPolicies)<BR>[getPreventionPolicies](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#getPreventionPolicies)<BR>[queryCombinedPreventionPolicies](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#queryCombinedPreventionPolicies)
## USAGE
### Find existing Prevention policies
```powershell
Get-FalconPreventionPolicy -All [-Detailed]
```

_2023-04-25: PSFalcon v2.2.5_
