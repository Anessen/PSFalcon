# Remove-FalconFileVantagePolicy
## SYNOPSIS
Remove FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|FileVantage policy identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFileVantagePolicy [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /filevantage/entities/policies/v1
```
### falconpy
[deletePolicies](https://github.com/CrowdStrike/falconpy/wiki/filevantage#deletePolicies)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
