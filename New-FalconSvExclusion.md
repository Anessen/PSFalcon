# New-FalconSvExclusion
## SYNOPSIS
Create a Sensor Visibility exclusion
## DESCRIPTION
Requires 'Sensor Visibility Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Value|String|RegEx pattern value|||||X|
|GroupId|Object[]|Host group identifier or 'all' to apply to all hosts|||||X|
|Comment|String|Audit log comment|||||X|
## SYNTAX
```powershell
New-FalconSvExclusion [-Value] <String> [-GroupId] <Object[]> [[-Comment] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/sv-exclusions/v1
```
### falconpy
[createSVExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/sensor-visibility-exclusions#createSVExclusionsV1)
## USAGE
### Create Sensor Visibility exclusions
```powershell
New-FalconSvExclusion -Value '/foo' -GroupId all -Comment 'creating'
```

_2023-04-25: PSFalcon v2.2.5_
