# Edit-FalconContainerAzureAccount
## SYNOPSIS
Modify the client identifier for a Falcon Container Security Azure account
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ClientId|String|Azure client identifier||||||
|Id|String|Azure tenant identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconContainerAzureAccount [-ClientId] <String> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /kubernetes-protection/entities/service-principal/azure/v1
```
### falconpy
[PatchAzureServicePrincipal](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#PatchAzureServicePrincipal)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
