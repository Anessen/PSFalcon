# New-FalconIoaExclusion
## SYNOPSIS
Create an Indicator of Attack exclusion
## DESCRIPTION
'ConvertTo-FalconIoaExclusion' can be used to generate the required Indicator of Attack exclusion properties
using an existing detection.

Requires 'IOA Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Exclusion name|||||X|
|PatternId|String|Indicator of Attack pattern identifier|||||X|
|PatternName|String|Indicator of Attack pattern name|||||X|
|ClRegex|String|Command line RegEx|||||X|
|IfnRegex|String|Image Filename RegEx|||||X|
|GroupId|Object[]|Host group identifier, or leave undefined to apply to all hosts|||||X|
|Description|String|Exclusion description|||||X|
|Comment|String|Audit log comment|||||X|
## SYNTAX
```powershell
New-FalconIoaExclusion [-Name] <String> [-PatternId] <String> [-PatternName] <String> [-ClRegex] <String> [-IfnRegex] <String> [[-GroupId] <Object[]>] [[-Description] <String>] [[-Comment] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/ioa-exclusions/v1
```
### falconpy
[createIOAExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ioa-exclusions#createIOAExclusionsV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
