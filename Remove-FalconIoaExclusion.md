# Remove-FalconIoaExclusion
## SYNOPSIS
Remove Indicator of Attack exclusions
## DESCRIPTION
Requires 'IOA Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Audit log comment||||||
|Id|String[]|Exclusion identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconIoaExclusion [[-Comment] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/ioa-exclusions/v1
```
### falconpy
[deleteIOAExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ioa-exclusions#deleteIOAExclusionsV1)
## USAGE
### Delete IOA exclusions
```powershell
Remove-FalconIoaExclusion -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
