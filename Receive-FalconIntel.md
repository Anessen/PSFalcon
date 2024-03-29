# Receive-FalconIntel
## SYNOPSIS
Download an intelligence report
## DESCRIPTION
Requires 'Reports (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path [default: <slug>.pdf]|||||X|
|Id|String|Report identifier|||||X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconIntel [[-Path] <String>] [-Id] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/entities/report-files/v1
```
### falconpy
[GetIntelReportPDF](https://github.com/CrowdStrike/falconpy/wiki/intel#GetIntelReportPDF)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
