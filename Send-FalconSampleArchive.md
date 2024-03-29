# Send-FalconSampleArchive
## SYNOPSIS
Upload an archive containing sample files.

Once upload has been completed, use the returned 'sha256' value with 'Expand-FalconSampleArchive' to extract files
for submission to Falcon Intelligence Sandbox or QuickScan.
## DESCRIPTION
Requires 'Sample uploads: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|IsConfidential|Boolean|Prohibit sample(s) from being displayed in MalQuery [default: True]||||||
|Comment|String|Audit log comment||||||
|Password|String|Password to extract files from archive||||||
|Name|String|File name||||||
|Path|String|Path to local file|||||X|
## SYNTAX
```powershell
Send-FalconSampleArchive [[-IsConfidential] <Boolean>] [[-Comment] <String>] [[-Password] <String>] [[-Name] <String>] [-Path] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /archives/entities/archives/v2
```
### falconpy
[ArchiveUploadV2](https://github.com/CrowdStrike/falconpy/wiki/archives#ArchiveUploadV2)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
