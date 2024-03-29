# Get-FalconIoaPlatform
## SYNOPSIS
Search for custom Indicator of Attack platforms
## DESCRIPTION
Requires 'Custom IOA rules: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Platform|||`windows`<BR>`mac`<BR>`linux`|X|X|
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIoaPlatform [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoaPlatform -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ioarules/entities/platforms/v1
GET /ioarules/queries/platforms/v1
```
### falconpy
[query_platformsMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#query_platformsMixin0)<BR>[get_platformsMixin0](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#get_platformsMixin0)
## USAGE
### Find custom IOA platforms
```powershell
Get-FalconIoaPlatform [-Detailed]
```

_2023-04-25: PSFalcon v2.2.5_
