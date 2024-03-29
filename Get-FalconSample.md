# Get-FalconSample
## SYNOPSIS
Retrieve detailed information about accessible sample files
## DESCRIPTION
Requires 'Sample uploads: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Sha256 hash value||||X|X|
## SYNTAX
```powershell
Get-FalconSample [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /samples/queries/samples/GET/v1
```
### falconpy
[QuerySampleV1](https://github.com/CrowdStrike/falconpy/wiki/sample-upload#QuerySampleV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
