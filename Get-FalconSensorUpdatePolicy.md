# Get-FalconSensorUpdatePolicy
## SYNOPSIS
Search for Sensor Update policies
## DESCRIPTION
Requires 'Sensor update policies: Read'.
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
Get-FalconSensorUpdatePolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSensorUpdatePolicy -Id <String[]> [[-Include] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSensorUpdatePolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/sensor-update/v2
GET /policy/entities/sensor-update/v2
GET /policy/queries/sensor-update/v1
```
### falconpy
[querySensorUpdatePolicies](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#querySensorUpdatePolicies)<BR>[getSensorUpdatePoliciesV2](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#getSensorUpdatePoliciesV2)<BR>[queryCombinedSensorUpdatePoliciesV2](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#queryCombinedSensorUpdatePoliciesV2)
## USAGE
### Retrieve detailed Windows policies
```powershell
Get-FalconSensorUpdatePolicy -Filter "platform_name:'Windows'" -Detailed
```

_2023-04-25: PSFalcon v2.2.5_
