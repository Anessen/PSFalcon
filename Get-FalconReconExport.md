# Get-FalconReconExport
## SYNOPSIS
Return status of Falcon Intelligence Recon export jobs
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Recon export job identifier||||X|X|
## SYNTAX
```powershell
Get-FalconReconExport [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /recon/entities/exports/v1
```
### falconpy
[GetExportJobsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetExportJobsV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
