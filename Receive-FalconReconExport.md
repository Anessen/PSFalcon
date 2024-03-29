# Receive-FalconReconExport
## SYNOPSIS
Download a Falcon Intelligence Recon export
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Id|String|Recon export job identifier||||X|X|
## SYNTAX
```powershell
Receive-FalconReconExport [-Path] <String> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /recon/entities/export-files/v1
```
### falconpy
[GetFileContentForExportJobsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetFileContentForExportJobsV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
