# Group-FalconMalQuerySample
## SYNOPSIS
Schedule MalQuery samples for download
## DESCRIPTION
Requires 'MalQuery: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Sha256 hash value||||X|X|
## SYNTAX
```powershell
Group-FalconMalQuerySample [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /malquery/entities/samples-multidownload/v1
```
### falconpy
[PostMalQueryEntitiesSamplesMultidownloadV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#PostMalQueryEntitiesSamplesMultidownloadV1)
## USAGE
### Download an archive of multiple MalQuery samples
```powershell
$Request = Group-FalconMalQuerySample -Id <sha256>, <sha256>
Receive-FalconMalQuerySample -Id $Request.reqid -Path .\infected.zip
```

_2023-04-25: PSFalcon v2.2.5_
