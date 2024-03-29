# Get-FalconIdentityHost
## SYNOPSIS
Search for Falcon Identity hosts
## DESCRIPTION
Requires 'Identity Protection Entities: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`200`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIdentityHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIdentityHost -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /identity-protection/queries/devices/v1
POST /identity-protection/entities/devices/GET/v1
```
### falconpy
[QuerySensorsByFilter](https://github.com/CrowdStrike/falconpy/wiki/identity-protection#QuerySensorsByFilter)<BR>[GetSensorDetails](https://github.com/CrowdStrike/falconpy/wiki/identity-protection#GetSensorDetails)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
