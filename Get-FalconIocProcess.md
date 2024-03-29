# Get-FalconIocProcess
## SYNOPSIS
Search for processes involving a custom indicator on a specific host
## DESCRIPTION
Requires 'IOCs: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Process identifier||||X||
|Type|String|Indicator type|||`domain`<BR>`ipv4`<BR>`ipv6`<BR>`md5`<BR>`sha256`|||
|Value|String|Indicator value||||||
|HostId|String|Host identifier||||X||
|Limit|String|Maximum number of results per request|`1`|`100`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
## SYNTAX
```powershell
Get-FalconIocProcess [-Type] <String> [-Value] <String> [-HostId] <String> [[-Limit] <String>] [-Offset <Int32>] [-Detailed] [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconIocProcess -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /indicators/queries/processes/v1
GET /processes/entities/processes/v1
```
### falconpy
[ProcessesRanOn](https://github.com/CrowdStrike/falconpy/wiki/ioc#ProcessesRanOn)<BR>[entities_processes](https://github.com/CrowdStrike/falconpy/wiki/processes#entities_processes)
## USAGE
### Finding process IDs of an IOC found on a host
```powershell
Get-FalconIocProcess -Type <string> -Value <string> -HostId <id> [-Detailed]
```
### Getting process details
```powershell
Get-FalconIocProcess -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
