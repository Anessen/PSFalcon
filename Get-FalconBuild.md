# Get-FalconBuild
## SYNOPSIS
Retrieve Falcon Sensor builds for assignment in Sensor Update policies
## DESCRIPTION
Requires 'Sensor update policies: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Platform|String|Operating system platform|||`linux`<BR>`mac`<BR>`windows`|||
|Stage|String[]|Sensor release stage|||`early_adopter`<BR>`prod`|||
## SYNTAX
```powershell
Get-FalconBuild [[-Platform] <String>] [[-Stage] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/sensor-update-builds/v1
```
### falconpy
[queryCombinedSensorUpdateBuilds](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#queryCombinedSensorUpdateBuilds)
## USAGE
### Retrieve a list of available sensor versions
```powershell
Get-FalconBuild
```
### Retrieve a list of available Windows sensor versions
```powershell
Get-FalconBuild -Platform windows
```

_2023-11-27: PSFalcon v2.2.6_
