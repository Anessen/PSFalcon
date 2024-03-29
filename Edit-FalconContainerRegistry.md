# Edit-FalconContainerRegistry
## SYNOPSIS
Modify a registry within Falcon Container Security
## DESCRIPTION
Requires 'Falcon Container Image: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Falcon Container Security registry name||||||
|State|String|Registry connection state|||`pause`<BR>`resume`|||
|Credential|Hashtable|A hashtable containing credentials to access the registry||||||
|Id|String|Container registry identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconContainerRegistry [[-Name] <String>] [[-State] <String>] [[-Credential] <Hashtable>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /container-security/entities/registries/v1
```
### falconpy
[UpdateRegistryEntities](https://github.com/CrowdStrike/falconpy/wiki/falcon-container#UpdateRegistryEntities)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
