# Remove-FalconContainerRegistry
## SYNOPSIS
Remove a registry from Falcon Container Security
## DESCRIPTION
Requires 'Falcon Container Image: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Container registry identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconContainerRegistry -Id <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /container-security/entities/registries/v1
```
### falconpy
[DeleteRegistryEntities](https://github.com/CrowdStrike/falconpy/wiki/falcon-container#DeleteRegistryEntities)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
