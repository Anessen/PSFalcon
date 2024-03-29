# New-FalconContainerAzureAccount
## SYNOPSIS
Provision Falcon Container Security Azure accounts
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SubscriptionId|String|Azure subscription identifier||||||
|TenantId|String|Azure tenant identifier||||||
## SYNTAX
```powershell
New-FalconContainerAzureAccount [[-SubscriptionId] <String>] [[-TenantId] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /kubernetes-protection/entities/accounts/azure/v1
```
### falconpy
[CreateAzureSubscription](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#CreateAzureSubscription)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
