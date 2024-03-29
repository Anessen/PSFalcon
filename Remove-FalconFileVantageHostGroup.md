# Remove-FalconFileVantageHostGroup
## SYNOPSIS
Remove host groups from FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PolicyId|String|FileVantage policy identifier||||||
|Id|String[]|Host group identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconFileVantageHostGroup [-PolicyId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/policies-host-groups/v1
```
### falconpy
[updatePolicyHostGroups](https://github.com/CrowdStrike/falconpy/wiki/host-group#updatePolicyHostGroups)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
