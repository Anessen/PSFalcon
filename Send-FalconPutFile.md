# Send-FalconPutFile
## SYNOPSIS
Upload a Real-time Response 'put' file
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|File name|`1`|`32766`|||X|
|Description|String|File description||||||
|Comment|String|Comment for audit log|`1`|`4096`||||
|Path|String|Path to local file|||||X|
## SYNTAX
```powershell
Send-FalconPutFile [[-Name] <String>] [[-Description] <String>] [[-Comment] <String>] [-Path] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/entities/put-files/v1
```
### falconpy
[RTR_CreatePut_Files](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_CreatePut_Files)
## USAGE
### Create a new 'put' file
```powershell
Send-FalconPutFile -Path .\File.exe
```
### Upload multiple 'put' files from a local directory
```powershell
Get-ChildItem C:\tools\*.exe | Send-FalconPutFile
```

_2023-11-27: PSFalcon v2.2.6_
