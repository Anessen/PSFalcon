# Receive-FalconInstaller
## SYNOPSIS
Download a Falcon sensor installer
## DESCRIPTION
Requires 'Sensor Download: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path|||||X|
|Id|String|Sha256 hash value||||X|X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconInstaller [-Path] <String> [-Id] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /sensors/entities/download-installer/v1
```
### falconpy
[DownloadSensorInstallerById](https://github.com/CrowdStrike/falconpy/wiki/sensor-download#DownloadSensorInstallerById)
## USAGE
```powershell
Receive-FalconInstaller -Id <id> -Path .\WindowsSensor.exe
```
_See [Download the installer package assigned to a Sensor Update policy](https://github.com/CrowdStrike/psfalcon/blob/master/samples/sensor_installers/download-the-installer-package-assigned-to-a-sensor-update-policy.ps1)._

_See [Download the installer package assigned to your default Sensor Update policy](https://github.com/CrowdStrike/psfalcon/blob/master/samples/sensor_installers/download-the-installer-package-assigned-to-your-default-sensor-update-policy.ps1)._

_2023-04-25: PSFalcon v2.2.5_
