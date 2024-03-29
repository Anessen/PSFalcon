# Receive-FalconMemoryDump
## SYNOPSIS
Download a memory dump or extracted strings from a Falcon Intelligence Sandbox report
## DESCRIPTION
Requires 'Sandbox (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|BinaryId|String|Binary content dump identifier||||X|X|
|ExtractId|String|Extracted string identifier|||||X|
|HexId|String|Hex dump identifier|||||X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconMemoryDump [[-Path] <String>] [-BinaryId] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Receive-FalconMemoryDump [[-Path] <String>] [-HexId] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Receive-FalconMemoryDump [[-Path] <String>] [-ExtractId] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falconx/entities/memory-dump/extracted-strings/v1
GET /falconx/entities/memory-dump/hex-dump/v1
GET /falconx/entities/memory-dump/v1
```
### falconpy
[GetMemoryDump](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#GetMemoryDump)<BR>[GetMemoryDumpHexDump](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#GetMemoryDumpHexDump)<BR>[GetMemoryDumpExtractedStrings](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#GetMemoryDumpExtractedStrings)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
