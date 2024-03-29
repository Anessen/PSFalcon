# Remove-FalconReconExport
## SYNOPSIS
Remove a Falcon Intelligence Recon export job
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Recon export job identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconReconExport [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /recon/entities/exports/v1
```
### falconpy
[DeleteExportJobsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#DeleteExportJobsV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
