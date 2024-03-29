# Expand-FalconSampleArchive
## SYNOPSIS
Extract files from an uploaded sample archive to make them available for analysis.

Use the returned 'id' with 'Get-FalconSampleExtraction' to retrieve extraction status.
## DESCRIPTION
Requires 'Sample uploads: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ExtractAll|Boolean|Extract all files from sample [default: True]||||||
|File|Object[]|Object(s) containing 'name', 'comment', and 'is_confidential' for uniquely handling individual files||||||
|Id|String|Sample archive identifier||||X|X|
## SYNTAX
```powershell
Expand-FalconSampleArchive [[-ExtractAll] <Boolean>] [[-File] <Object[]>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /archives/entities/extractions/v1
```
### falconpy
[ExtractionCreateV1](https://github.com/CrowdStrike/falconpy/wiki/archives#ExtractionCreateV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
