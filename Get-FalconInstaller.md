# Get-FalconInstaller
## SYNOPSIS
Search for Falcon sensor installers
## DESCRIPTION
Requires 'Sensor Download: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Sha256 hash value||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconInstaller [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconInstaller -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconInstaller [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /sensors/combined/installers/v1
GET /sensors/entities/installers/v1
GET /sensors/queries/installers/v1
```
### falconpy
[GetSensorInstallersByQuery](https://github.com/CrowdStrike/falconpy/wiki/sensor-download#GetSensorInstallersByQuery)<BR>[GetSensorInstallersEntities](https://github.com/CrowdStrike/falconpy/wiki/sensor-download#GetSensorInstallersEntities)<BR>[GetCombinedSensorInstallersByQuery](https://github.com/CrowdStrike/falconpy/wiki/sensor-download#GetCombinedSensorInstallersByQuery)
## USAGE
### Find all available sensor installers for Linux
```powershell
Get-FalconInstaller -Filter "platform:'linux'" [-Detailed] [-All]
```
### Find all available sensor installers for a specific OS version
```powershell
Get-FalconInstaller -Filter "os:'Amazon Linux'" [-Detailed] [-All]
```
### Retrieve detailed information about a specific sensor installer
```powershell
Get-FalconInstaller -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
