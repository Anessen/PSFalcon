# Get-FalconContainerCluster
## SYNOPSIS
Search for Falcon Container Security clusters
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Cluster account identifier||||X|X|
|Location|String[]|Cloud provider location||||||
|ClusterName|String[]|Cluster name||||||
|ClusterService|String|Cluster service|||`eks`|||
|Status|String[]|Cluster Status|||`Not Installed`<BR>`Running`<BR>`Stopped`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconContainerCluster [[-Id] <String[]>] [[-Location] <String[]>] [[-ClusterName] <String[]>] [[-ClusterService] <String>] [[-Status] <String[]>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/kubernetes/clusters/v1
```
### falconpy
[GetClusters](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetClusters)
## USAGE
### List acknowledged clusters
```powershell
Get-FalconContainerCluster -ClusterService eks
```

_2023-11-27: PSFalcon v2.2.6_
