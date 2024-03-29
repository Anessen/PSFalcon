# Get-FalconQuarantine
## SYNOPSIS
Search for quarantined files
## DESCRIPTION
Requires 'Quarantined Files: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Quarantined file identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Match phrase prefix||||||
|Sort|String|Property and direction to sort results|||`hostname.asc`<BR>`hostname.desc`<BR>`username.asc`<BR>`username.desc`<BR>`date_updated.asc`<BR>`date_updated.desc`<BR>`date_created.asc`<BR>`date_created.desc`<BR>`paths.path.asc`<BR>`paths.path.desc`<BR>`paths.state.asc`<BR>`paths.state.desc`<BR>`state.asc`<BR>`state.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconQuarantine [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconQuarantine -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /quarantine/queries/quarantined-files/v1
POST /quarantine/entities/quarantined-files/GET/v1
```
### falconpy
[QueryQuarantineFiles](https://github.com/CrowdStrike/falconpy/wiki/quarantine#QueryQuarantineFiles)<BR>[GetQuarantineFiles](https://github.com/CrowdStrike/falconpy/wiki/quarantine#GetQuarantineFiles)
## USAGE
### Find quarantined files using a filtered search
```powershell
Get-FalconQuarantine -Filter "device.hostname:'EXAMPLE-PC'"
```
### Find information about specific quarantined files
```powershell
Get-FalconQuarantine -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
