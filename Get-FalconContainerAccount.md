# Get-FalconContainerAccount
## SYNOPSIS
Return provisioned Falcon Container Security accounts and known clusters
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Cluster account identifier||||X|X|
|Location|String[]|Cloud provider location||||||
|ClusterService|String[]|Cluster service|||`aks`<BR>`eks`|||
|ClusterStatus|String[]|Cluster status|||`Not Installed`<BR>`Running`<BR>`Stopped`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconContainerAccount [[-Id] <String[]>] [[-Location] <String[]>] [[-ClusterService] <String[]>] [[-ClusterStatus] <String[]>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/cloud_cluster/v1
```
### falconpy
[GetCombinedCloudClusters](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetCombinedCloudClusters)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
