# Get-FalconContainerSensor
## SYNOPSIS
Retrieve the most recent Falcon container sensor build tags
## DESCRIPTION
Requires 'Falcon Container Image: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|LatestUrl|Switch|Create a URL using the most recent build tag||||||
## SYNTAX
```powershell
Get-FalconContainerSensor [-LatestUrl] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /v2/{sensortype}/{region}/release/falcon-sensor/tags/list
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
