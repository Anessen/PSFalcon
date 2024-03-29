# Stop-FalconScan
## SYNOPSIS
Stop an on-demand scan
## DESCRIPTION
Requires 'On-demand scans (ODS): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|On-demand scan identifier||||X|X|
## SYNTAX
```powershell
Stop-FalconScan -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /ods/entities/scan-control-actions/cancel/v1
```
### falconpy
[cancel_scans](https://github.com/CrowdStrike/falconpy/wiki/ods#cancel_scans)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
