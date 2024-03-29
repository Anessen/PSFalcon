# Remove-FalconSvExclusion
## SYNOPSIS
Remove Sensor Visibility exclusions
## DESCRIPTION
Requires 'Sensor Visibility Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Audit log comment||||||
|Id|String[]|Exclusion identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconSvExclusion [[-Comment] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/sv-exclusions/v1
```
### falconpy
[deleteSensorVisibilityExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/sensor-visibility-exclusions#deleteSensorVisibilityExclusionsV1)
## USAGE
### Delete Sensor Visibility exclusions
```powershell
Remove-FalconSvExclusion -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
