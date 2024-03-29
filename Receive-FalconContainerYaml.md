# Receive-FalconContainerYaml
## SYNOPSIS
Download a sample Helm values.yaml file
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ClusterName|String|Cluster name||||X|X|
|IsSelfManagedCluster|Boolean|Restrict results to clusters that are not managed by the cloud provider||||||
|Path|String|Destination path||||||
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconContainerYaml [-ClusterName] <String> [[-IsSelfManagedCluster] <Boolean>] [-Path] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/integration/agent/v1
```
### falconpy
[GetHelmValuesYaml](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetHelmValuesYaml)
## USAGE
### Generate sample Helm values file
```powershell
Receive-FalconContainerYaml -ClusterName <string> -Path .\values.yaml
```

_2023-11-27: PSFalcon v2.2.6_
