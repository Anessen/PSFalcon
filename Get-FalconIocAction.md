# Get-FalconIocAction
## SYNOPSIS
Search for custom indicator actions
## DESCRIPTION
Requires 'IOC Manager APIs: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Custom indicator action identifier||||X|X|
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
## SYNTAX
```powershell
Get-FalconIocAction [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIocAction [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /iocs/entities/actions/v1
GET /iocs/queries/actions/v1
```
### falconpy
[action_query_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#action_query_v1)<BR>[action_get_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#action_get_v1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
