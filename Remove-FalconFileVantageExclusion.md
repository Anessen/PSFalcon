# Remove-FalconFileVantageExclusion
## SYNOPSIS
Remove scheduled exclusions from FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PolicyId|String|FileVantage policy identifier||||||
|Id|String[]|FileVantage scheduled exclusion identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFileVantageExclusion [-PolicyId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /filevantage/entities/policy-scheduled-exclusions/v1
```
### falconpy
[deleteScheduledExclusions](https://github.com/CrowdStrike/falconpy/wiki/filevantage#deleteScheduledExclusions)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
