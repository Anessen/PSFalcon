# Get-FalconContainerAzureConfig
## SYNOPSIS
Return Falcon Container Security Azure tenant configurations
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Azure tenant identifier||||X|X|
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconContainerAzureConfig [[-Id] <String[]>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/config/azure/v1
```
### falconpy
[GetAzureTenantConfig](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetAzureTenantConfig)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
