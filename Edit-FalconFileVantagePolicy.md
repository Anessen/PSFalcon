# Edit-FalconFileVantagePolicy
## SYNOPSIS
Modify FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|FileVantage policy identifier|||||X|
|Name|String|Policy name|`1`|`100`|||X|
|Enabled|Boolean|Policy enablement status|||||X|
|Description|String|Policy description||`500`|||X|
## SYNTAX
```powershell
Edit-FalconFileVantagePolicy [-Id] <String> [[-Name] <String>] [[-Enabled] <Boolean>] [[-Description] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/policies/v1
```
### falconpy
[updatePolicies](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updatePolicies)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
