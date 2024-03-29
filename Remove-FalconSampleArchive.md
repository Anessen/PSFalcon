# Remove-FalconSampleArchive
## SYNOPSIS
Delete a sample archive
## DESCRIPTION
Requires 'Sample uploads: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Sample archive identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconSampleArchive [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /archives/entities/archives/v1
```
### falconpy
[ArchiveDeleteV1](https://github.com/CrowdStrike/falconpy/wiki/archives#ArchiveDeleteV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
