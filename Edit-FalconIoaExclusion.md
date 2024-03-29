# Edit-FalconIoaExclusion
## SYNOPSIS
Modify an Indicator of Attack exclusion
## DESCRIPTION
Requires 'IOA Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Exclusion name|||||X|
|ClRegex|String|Command line RegEx|||||X|
|IfnRegex|String|Image Filename RegEx|||||X|
|GroupId|Object[]|Host group identifier or 'all' to apply to all hosts|||||X|
|Description|String|Exclusion description|||||X|
|Comment|String|Audit log comment|||||X|
|PatternId|String|Indicator of Attack pattern identifier|||||X|
|PatternName|String|Indicator of Attack pattern name|||||X|
|Id|String|Exclusion identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconIoaExclusion [[-Name] <String>] [[-ClRegex] <String>] [[-IfnRegex] <String>] [[-GroupId] <Object[]>] [[-Description] <String>] [[-Comment] <String>] [[-PatternId] <String>] [[-PatternName] <String>] -Id <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/ioa-exclusions/v1
```
### falconpy
[updateIOAExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ioa-exclusions#updateIOAExclusionsV1)
## USAGE
### Modify IOA exclusions
```powershell
Edit-FalconIoaExclusion -Id <id> -ImagePath '.*\\Windows\\System32\\choice1\.exe'
```

_2023-04-25: PSFalcon v2.2.5_
