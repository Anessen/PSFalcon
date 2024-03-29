# Get-FalconKernel
## SYNOPSIS
Search for Falcon kernel compatibility information for Sensor builds
## DESCRIPTION
Requires 'Sensor update policies: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Field|String|Return values for a specific field|||`architecture`<BR>`base_package_supported_sensor_versions`<BR>`distro`<BR>`distro_version`<BR>`flavor`<BR>`release`<BR>`vendor`<BR>`version`<BR>`ztl_supported_sensor_versions`|||
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`architecture.asc`<BR>`architecture.desc`<BR>`distro.asc`<BR>`distro.desc`<BR>`distro_version.asc`<BR>`distro_version.desc`<BR>`flavor.asc`<BR>`flavor.desc`<BR>`release.asc`<BR>`release.desc`<BR>`vendor.asc`<BR>`vendor.desc`<BR>`version.asc`<BR>`version.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconKernel [[-Filter] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconKernel [-Field] <String> [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/sensor-update-kernels/v1
GET /policy/queries/sensor-update-kernels/{distinct-field}/v1
```
### falconpy
[queryCombinedSensorUpdateKernels](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#queryCombinedSensorUpdateKernels)<BR>[querySensorUpdateKernelsDistinct](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#querySensorUpdateKernelsDistinct)
## USAGE
### List results of a filtered search
```powershell
Get-FalconKernel -Filter "vendor:'ubuntu'+distro:'ubuntu20'+flavor:'gcp'+release:*'5.8.*'"
```
### Retrieve distro values
```powershell
Get-FalconKernel -Field distro -Sort vendor.asc
```

_2023-11-27: PSFalcon v2.2.6_
