# Remove-FalconSample
## SYNOPSIS
Remove a sample
## DESCRIPTION
Requires 'Sample uploads: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Sha256 hash value||||X|X|
## SYNTAX
```powershell
Remove-FalconSample [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /samples/entities/samples/v3
```
### falconpy
[DeleteSampleV3](https://github.com/CrowdStrike/falconpy/wiki/sample-upload#DeleteSampleV3)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
