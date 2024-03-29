# New-FalconMlExclusion
## SYNOPSIS
Create a Machine Learning exclusion
## DESCRIPTION
'ConvertTo-FalconMlExclusion' can be used to generate the required Machine Learning exclusion properties using
an existing detection.

Requires 'Machine Learning Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Value|String|RegEx pattern value|||||X|
|ExcludedFrom|String[]|Actions to exclude|||`blocking`<BR>`extraction`||X|
|GroupId|Object[]|Host group identifier or 'all' to apply to all hosts|||||X|
|Comment|String|Audit log comment|||||X|
## SYNTAX
```powershell
New-FalconMlExclusion [-Value] <String> [-ExcludedFrom] <String[]> [-GroupId] <Object[]> [[-Comment] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/ml-exclusions/v1
```
### falconpy
[createMLExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/ml-exclusions#createMLExclusionsV1)
## USAGE
### Create Machine Learning exclusions
```powershell
New-FalconMlExclusion -Value '/foo' -ExcludedFrom blocking, extraction -GroupId all -Comment 'creating foo'
```

_2023-04-25: PSFalcon v2.2.5_
