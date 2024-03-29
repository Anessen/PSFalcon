# Edit-FalconSvExclusion
## SYNOPSIS
Modify a Sensor Visibility exclusion
## DESCRIPTION
Requires 'Sensor Visibility Exclusions: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Value|String|RegEx pattern value|||||X|
|GroupId|Object[]|Host group identifier or 'all' to apply to all hosts|||||X|
|Comment|String|Audit log comment|||||X|
|Id|String|Exclusion identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconSvExclusion [[-Value] <String>] [[-GroupId] <Object[]>] [[-Comment] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/sv-exclusions/v1
```
### falconpy
[updateSensorVisibilityExclusionsV1](https://github.com/CrowdStrike/falconpy/wiki/sensor-visibility-exclusions#updateSensorVisibilityExclusionsV1)
## USAGE
### Modify Sensor Visibility exclusions
```powershell
Edit-FalconSvExclusion -Id <id> -Value '/foochanged*'
```
_See [Modify all Sensor Visibility exclusions to include an additional Host Group](https://github.com/CrowdStrike/psfalcon/blob/master/samples/policies/modify-all-sensor-visibility-exclusions-to-include-an-additional-host-group.ps1)._

_2023-04-25: PSFalcon v2.2.5_
