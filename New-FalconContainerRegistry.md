# New-FalconContainerRegistry
## SYNOPSIS
Create a registry within Falcon Container Security
## DESCRIPTION
Requires 'Falcon Container Image: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Desired registry name within Falcon Container Security||||||
|Type|String|Registry type|||`acr`<BR>`artifactory`<BR>`docker`<BR>`dockerhub`<BR>`ecr`<BR>`gar`<BR>`gcr`<BR>`github`<BR>`gitlab`<BR>`harbor`<BR>`icr`<BR>`mirantis`<BR>`nexus`<BR>`openshift`<BR>`oracle`<BR>`quay.io`|||
|Url|String|UniquenessKey<BR>Registry URL alias<BR><BR>Available with Docker Hub, Google Artifact Registry, Google Container Registry, IBM Cloud, and Oracle||||||
|Credential|Hashtable|A hashtable containing credentials to access the registry||||||
|UrlUniquenessKey|String|Registry URL alias<BR><BR>Available with Docker Hub, Google Artifact Registry, Google Container Registry, IBM Cloud, and Oracle||||||
## SYNTAX
```powershell
New-FalconContainerRegistry [-Name] <String> [-Type] <String> [-Url] <String> [-Credential] <Hashtable> [[-UrlUniquenessKey] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /container-security/entities/registries/v1
```
### falconpy
[CreateRegistryEntities](https://github.com/CrowdStrike/falconpy/wiki/falcon-container#CreateRegistryEntities)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
