# Receive-FalconMalQuerySample
## SYNOPSIS
Download a sample or sample archive from Falcon MalQuery [password: 'infected']
## DESCRIPTION
Requires 'MalQuery: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Id|String|Sha256 hash value or MalQuery sample archive identifier||||X|X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconMalQuerySample [-Path] <String> [-Id] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /malquery/entities/download-files/v1
```
### falconpy
[GetMalQueryDownloadV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#GetMalQueryDownloadV1)
## USAGE
### Download a MalQuery sample
```powershell
Receive-FalconMalQuerySample -Id <sha256> -Path .\infected.exe
```

_2023-04-25: PSFalcon v2.2.5_
