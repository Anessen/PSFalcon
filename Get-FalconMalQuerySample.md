# Get-FalconMalQuerySample
## SYNOPSIS
Retrieve Falcon MalQuery indexed file metadata
## DESCRIPTION
Requires 'MalQuery: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Sha256 hash value||||X|X|
## SYNTAX
```powershell
Get-FalconMalQuerySample [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /malquery/entities/metadata/v1
```
### falconpy
[GetMalQueryMetadataV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#GetMalQueryMetadataV1)
## USAGE
### Retrieve MalQuery sample metadata
```powershell
Get-FalconMalQuerySample -Id <sha256>, <sha256>
```

_2023-04-25: PSFalcon v2.2.5_
