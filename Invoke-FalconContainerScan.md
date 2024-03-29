# Invoke-FalconContainerScan
## SYNOPSIS
Initiate a Falcon Container Security scan
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ScanType|String|Scan type|||`cluster-refresh`<BR>`dry-run`<BR>`full`|||
## SYNTAX
```powershell
Invoke-FalconContainerScan [-ScanType] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /kubernetes-protection/entities/scan/trigger/v1
```
### falconpy
[TriggerScan](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#TriggerScan)
## USAGE
### Initiate scan of Kubernetes footprint
```powershell
Invoke-FalconContainerScan -ScanType full
```

_2023-11-27: PSFalcon v2.2.6_
