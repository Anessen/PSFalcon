# Get-FalconIoaType
## SYNOPSIS
Search for custom Indicator of Attack types
## DESCRIPTION
Requires 'Custom IOA rules: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Type identifier||||X|X|
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconIoaType [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIoaType -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ioarules/entities/rule-types/v1
GET /ioarules/queries/rule-types/v1
```
### falconpy
[query_rule_types](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#query_rule_types)<BR>[get_rule_types](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#get_rule_types)
## USAGE
### Find custom IOA rule types
```powershell
Get-FalconIoaType [-Detailed]
```

_2023-04-25: PSFalcon v2.2.5_
