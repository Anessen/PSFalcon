# Get-FalconContainerRegistry
## SYNOPSIS
List Falcon Container Security registries
## DESCRIPTION
Requires 'Falcon Container Image: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Container registry identifier||||X|X|
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconContainerRegistry [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconContainerRegistry -Id <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /container-security/entities/registries/v1
GET /container-security/queries/registries/v1
```
### falconpy
[ReadRegistryEntities](https://github.com/CrowdStrike/falconpy/wiki/falcon-container#ReadRegistryEntities)<BR>[ReadRegistryEntitiesByUUID](https://github.com/CrowdStrike/falconpy/wiki/falcon-container#ReadRegistryEntitiesByUUID)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
