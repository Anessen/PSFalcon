# Get-FalconContainerAzureTenant
## SYNOPSIS
Return Falcon Container Security Azure tenants
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Azure tenant identifier||||X|X|
|Status|String|Cluster Status|||`Not Installed`<BR>`Running`<BR>`Stopped`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconContainerAzureTenant [[-Id] <String[]>] [[-Status] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/tenants/azure/v1
```
### falconpy
[GetAzureTenantIDs](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetAzureTenantIDs)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
