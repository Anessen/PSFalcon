# Remove-FalconMlExclusion
## SYNOPSIS
Remove Machine Learning exclusions
## DESCRIPTION
Requires 'Machine Learning Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Audit log comment||||||
|Id|String[]|Exclusion identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconMlExclusion [[-Comment] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/ml-exclusions/v1
```
### falconpy
[deleteMLExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ml-exclusions#deleteMLExclusionsV1)
## USAGE
### Delete Machine Learning exclusions
```powershell
Remove-FalconMlExclusion -Id <id>, <id>
```
```powershell
Get-FalconMlExclusion -Filter "applied_globally:True" | Remove-FalconMlExclusion
```

_2023-04-25: PSFalcon v2.2.5_
