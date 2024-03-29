# Get-FalconIocPlatform
## SYNOPSIS
List custom indicator platforms
## DESCRIPTION
Requires 'IOC Manager APIs: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
## SYNTAX
```powershell
Get-FalconIocPlatform [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /iocs/queries/platforms/v1
```
### falconpy
[platform_query_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#platform_query_v1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
