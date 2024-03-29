# Get-FalconInstallTokenEvent
## SYNOPSIS
Search for installation token audit events
## DESCRIPTION
Requires 'Installation tokens: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Installation token audit event identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconInstallTokenEvent [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconInstallTokenEvent -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /installation-tokens/entities/audit-events/v1
GET /installation-tokens/queries/audit-events/v1
```
### falconpy
[audit_events_query](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#audit_events_query)<BR>[audit_events_read](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#audit_events_read)
## USAGE
### View installation token audit events
```powershell
Get-FalconInstallTokenEvent [-Detailed] [-All]
```
### Get information about an installation token audit event
```powershell
Get-FalconInstallTokenEvent -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
