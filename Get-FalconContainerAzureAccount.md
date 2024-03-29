# Get-FalconContainerAzureAccount
## SYNOPSIS
Return Falcon Container Security Azure accounts
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Azure tenant identifier||||X|X|
|SubscriptionId|String[]|Azure subscription identifier||||||
|Status|String|Filter by account status|||`operational`<BR>`provisioned`|||
|IsHorizonAcct|Boolean|Filter by whether an account originates from Horizon or not||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconContainerAzureAccount [[-Id] <String[]>] [[-SubscriptionId] <String[]>] [[-Status] <String>] [[-IsHorizonAcct] <Boolean>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/accounts/azure/v1
```
### falconpy
[ListAzureAccounts](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#ListAzureAccounts)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
