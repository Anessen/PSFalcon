# Edit-FalconMlExclusion
## SYNOPSIS
Modify a Machine Learning exclusion
## DESCRIPTION
Requires 'Machine Learning Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Value|String|RegEx pattern value|||||X|
|GroupId|Object[]|Host group identifier or 'all' to apply to all hosts|||||X|
|Comment|String|Audit log comment|||||X|
|Id|String|Exclusion identifier|||||X|
## SYNTAX
```powershell
Edit-FalconMlExclusion [[-Value] <String>] [[-GroupId] <Object[]>] [[-Comment] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/ml-exclusions/v1
```
### falconpy
[updateMLExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ml-exclusions#updateMLExclusionsV1)
## USAGE
### Modify Machine Learning exclusions
```powershell
Edit-FalconMlExclusion -Id <id> -Value '/foo*'
```

_2023-04-25: PSFalcon v2.2.5_
