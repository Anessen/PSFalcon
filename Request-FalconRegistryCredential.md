# Request-FalconRegistryCredential
## SYNOPSIS
Request your Falcon container registry username, password and access token
## DESCRIPTION
If successful, you token and username are cached for re-use as you use Falcon container security related commands.

If an active access token is due to expire in less than 15 seconds, a new token will automatically be requested.

Requires 'Falcon Container Image: Read' and 'Sensor Download: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SensorType|String|Container sensor type, used to determine container registry|||`falcon-sensor`<BR>`falcon-container`|||
## SYNTAX
```powershell
Request-FalconRegistryCredential [-SensorType] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
