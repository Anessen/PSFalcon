# Receive-FalconGetFile
## SYNOPSIS
Download a password protected .7z archive containing a Real-time Response 'get' file [password: 'infected']
## DESCRIPTION
'Sha256' and 'SessionId' values can be found using 'Confirm-FalconGetFile'. 'Invoke-FalconResponderCommand' or
'Invoke-FalconAdminCommand' can be used to issue a 'get' command to a single-host, and 'Invoke-FalconBatchGet' can
be used for multiple hosts within existing Real-time Response session.

Requires 'Real time response: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Sha256|String|Sha256 hash value|||||X|
|SessionId|String|Session identifier|||||X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconGetFile [[-Path] <String>] [-Sha256] <String> [-SessionId] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /real-time-response/entities/extracted-file-contents/v1
```
### falconpy
[RTR_GetExtractedFileContents](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_GetExtractedFileContents)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
