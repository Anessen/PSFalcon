# Get-FalconContainerAzureScript
## SYNOPSIS
Return Falcon Container Security script
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Azure tenant identifier||||X|X|
|SubscriptionId|String[]|Azure subscription identifier||||||
## SYNTAX
```powershell
Get-FalconContainerAzureScript [-Id] <String> [[-SubscriptionId] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/user-script/azure/v1
```
### falconpy
[GetAzureInstallScript](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetAzureInstallScript)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
