# Get-FalconIocHost
## SYNOPSIS
Search for hosts that have observed a custom indicator
## DESCRIPTION
Requires 'IOCs: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Type|String|Indicator type|||`domain`<BR>`ipv4`<BR>`ipv6`<BR>`md5`<BR>`sha256`||X|
|Value|String|Indicator value|||||X|
|Limit|String|Maximum number of results per request|`1`|`100`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display the total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIocHost [-Type] <String> [-Value] <String> [[-Limit] <String>] [-Offset <Int32>] [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIocHost [-Type] <String> [-Value] <String> -Total [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /indicators/aggregates/devices-count/v1
GET /indicators/queries/devices/v1
```
### falconpy
[DevicesRanOn](https://github.com/CrowdStrike/falconpy/wiki/ioc#DevicesRanOn)<BR>[DevicesCount](https://github.com/CrowdStrike/falconpy/wiki/ioc#DevicesCount)
## USAGE
### Getting the host count
```powershell
Get-FalconIocHost -Type <string> -Value <string> -Total
```
### Getting the list of hosts that have seen an IOC
```powershell
Get-FalconIocHost -Type <string> -Value <string>
```

_2023-04-25: PSFalcon v2.2.5_
