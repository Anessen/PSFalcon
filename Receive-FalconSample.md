# Receive-FalconSample
## SYNOPSIS
Download a sample
## DESCRIPTION
Requires 'Sample uploads: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|PasswordProtected|Boolean|Archive and password protect the sample with password 'infected'||||||
|Id|String|Sha256 hash value||||X|X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconSample [-Path] <String> [[-PasswordProtected] <Boolean>] [-Id] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /samples/entities/samples/v3
```
### falconpy
[GetSampleV3](https://github.com/CrowdStrike/falconpy/wiki/sample-upload#GetSampleV3)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
