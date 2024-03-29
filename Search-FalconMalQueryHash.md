# Search-FalconMalQueryHash
## SYNOPSIS
Perform a simple Falcon MalQuery YARA Hunt for a Sha256 hash
## DESCRIPTION
Performs a YARA Hunt for the given hash, then checks every 5 seconds--for up to 60 seconds--for a result.

Requires 'MalQuery: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Sha256|String|Sha256 hash value||||X|X|
## SYNTAX
```powershell
Search-FalconMalQueryHash [-Sha256] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Perform a simple YARA search for a specific hash
**NOTE**: `Search-FalconMalQueryHash` which will run a simple YARA-based hash search to find a SHA256 value.
```powershell
Search-FalconMalQueryHash -Sha256 <sha256>
```

_2023-04-25: PSFalcon v2.2.5_
