# Get-FalconSampleArchive
## SYNOPSIS
Retrieve status for uploaded sample archives or a list of the files inside them
## DESCRIPTION
Requires 'Sample uploads: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|IncludeFiles|Boolean|Include list of file names||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|String|Position to begin retrieving results||||||
|Id|String|Sample archive identifier||||X|X|
|FileList|Switch|Return a list of files inside the sample archive||||||
## SYNTAX
```powershell
Get-FalconSampleArchive [[-IncludeFiles] <Boolean>] -Id <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSampleArchive [[-Limit] <Int32>] [-Offset <String>] -Id <String> -FileList [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /archives/entities/archive-files/v1
GET /archives/entities/archives/v1
```
### falconpy
[ArchiveGetV1](https://github.com/CrowdStrike/falconpy/wiki/archives#ArchiveGetV1)<BR>[ArchiveListV1](https://github.com/CrowdStrike/falconpy/wiki/archives#ArchiveListV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
