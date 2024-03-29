# New-FalconFileVantagePolicy
## SYNOPSIS
Create FileVantage policies
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Policy name|`1`|`100`|||X|
|Platform|String|Operating system platform|||`Linux`<BR>`Mac`<BR>`Windows`||X|
|Description|String|Policy description||`500`|||X|
## SYNTAX
```powershell
New-FalconFileVantagePolicy [-Name] <String> [[-Platform] <String>] [[-Description] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /filevantage/entities/policies/v1
```
### falconpy
[createPolicies](https://github.com/CrowdStrike/falconpy/wiki/filevantage#createPolicies)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
