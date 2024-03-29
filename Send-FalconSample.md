# Send-FalconSample
## SYNOPSIS
Upload a sample file
## DESCRIPTION
A successful upload will provide a 'sha256' value that can be used in submissions to the Falcon Sandbox or
Falcon QuickScan.

Maximum file size is 256MB. ZIP and 7z archives will automatically redirect to 'Send-FalconSampleArchive'.

Requires 'Sample uploads: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|IsConfidential|Boolean|Prohibit sample from being displayed in MalQuery [default: True]||||||
|Comment|String|Audit log comment||||||
|Name|String|File name|||||X|
|Path|String|Path to local file|||||X|
## SYNTAX
```powershell
Send-FalconSample [[-IsConfidential] <Boolean>] [[-Comment] <String>] [[-Name] <String>] [-Path] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /samples/entities/samples/v3
```
### falconpy
[UploadSampleV3](https://github.com/CrowdStrike/falconpy/wiki/sample-upload#UploadSampleV3)
## USAGE
### Upload a sample
```powershell
Send-FalconSample -Path C:\virus.exe -Filename virus.exe -Comment 'bad file'
```
### Upload a directory of samples
```powershell
Get-ChildItem -Path C:\samples -File | Send-FalconSample
```
_See [New-FalconQuickScan](New-FalconQuickScan)._

_See [New-FalconSubmission](New-FalconSubmission)._

_2023-04-25: PSFalcon v2.2.5_
