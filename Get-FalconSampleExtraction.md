# Get-FalconSampleExtraction
## SYNOPSIS
Retrieve status for sample archive extractions or the files inside them
## DESCRIPTION
Requires 'Sample uploads: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|IncludeFiles|Boolean|Include list of file names||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|String|Position to begin retrieving results||||||
|Id|String|Sample archive identifier||||X|X|
|FileList|Switch|Return the list of files extracted from the sample archive||||||
## SYNTAX
```powershell
Get-FalconSampleExtraction [[-IncludeFiles] <Boolean>] -Id <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSampleExtraction [[-Limit] <Int32>] [-Offset <String>] -Id <String> -FileList [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /archives/entities/extraction-files/v1
GET /archives/entities/extractions/v1
```
### falconpy
[ExtractionGetV1](https://github.com/CrowdStrike/falconpy/wiki/archives#ExtractionGetV1)<BR>[ExtractionListV1](https://github.com/CrowdStrike/falconpy/wiki/archives#ExtractionListV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
