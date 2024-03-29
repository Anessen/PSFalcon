# Get-FalconResponsePolicy
## SYNOPSIS
Search for Real-time Response policies
## DESCRIPTION
Requires 'Response policies: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`created_by`<BR>`created_timestamp`<BR>`description`<BR>`enabled`<BR>`groups`<BR>`modified_by`<BR>`modified_timestamp`<BR>`name`<BR>`name.raw`<BR>`platform_name`||||||
|Sort|String|Property and direction to sort results|||`created_by.asc`<BR>`created_by.desc`<BR>`created_timestamp.asc`<BR>`created_timestamp.desc`<BR>`enabled.asc`<BR>`enabled.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`<BR>`platform_name.asc`<BR>`platform_name.desc`<BR>`precedence.asc`<BR>`precedence.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Include|String[]|Include additional properties|||`members`|||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconResponsePolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconResponsePolicy -Id <String[]> [[-Include] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconResponsePolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/response/v1
GET /policy/entities/response/v1
GET /policy/queries/response/v1
```
### falconpy
[queryRTResponsePolicies](https://github.com/CrowdStrike/falconpy/wiki/response-policies#queryRTResponsePolicies)<BR>[getRTResponsePolicies](https://github.com/CrowdStrike/falconpy/wiki/response-policies#getRTResponsePolicies)<BR>[queryCombinedRTResponsePolicies](https://github.com/CrowdStrike/falconpy/wiki/response-policies#queryCombinedRTResponsePolicies)
## USAGE
### Find policy details using a filtered search
```powershell
Get-FalconResponsePolicy -Filter "name:'test'" -Sort modified_timestamp.asc -Detailed
```
### List policy ids using a filtered search
```powershell
Get-FalconResponsePolicy -Filter "created_by:'diana.hudson'" -Sort name.desc
```
### List details about specific policies
```powershell
Get-FalconResponsePolicy -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
