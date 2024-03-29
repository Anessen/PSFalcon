# Remove-FalconContainerAzureAccount
## SYNOPSIS
Remove Falcon Container Security Azure accounts
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Azure subscription identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconContainerAzureAccount [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /kubernetes-protection/entities/accounts/azure/v1
```
### falconpy
[DeleteAzureSubscription](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#DeleteAzureSubscription)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
