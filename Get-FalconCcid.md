# Get-FalconCcid
## SYNOPSIS
Retrieve your Falcon Customer Checksum Identifier (CCID)
## DESCRIPTION
Returns your Customer Checksum Identifier which is requested during the installation of the Falcon Sensor.

Requires 'Sensor Download: Read'.
## SYNTAX
```powershell
Get-FalconCcid [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /sensors/queries/installers/ccid/v1
```
### falconpy
[GetSensorInstallersCCIDByQuery](https://github.com/CrowdStrike/falconpy/wiki/sensor-download#GetSensorInstallersCCIDByQuery)
## USAGE
### Find your Customer ID and Checksum \(CCID\)
```powershell
Get-FalconCcid
```

_2023-04-25: PSFalcon v2.2.5_
