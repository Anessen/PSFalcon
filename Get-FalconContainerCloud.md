# Get-FalconContainerCloud
## SYNOPSIS
Return Falcon Container Security cloud provider locations
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Cloud|String[]|Cloud provider|||`aws`<BR>`azure`<BR>`gcp`|X|X|
## SYNTAX
```powershell
Get-FalconContainerCloud [[-Cloud] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/cloud-locations/v1
```
### falconpy
[GetLocations](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetLocations)
## USAGE
### List acknowledged cloud locations
```powershell
Get-FalconContainerCloud -Cloud aws
```

_2023-04-25: PSFalcon v2.2.5_
