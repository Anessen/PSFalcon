# Get-FalconContainerAwsAccount
## SYNOPSIS
Return Falcon Container Security AWS accounts
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|AWS account identifier||||X|X|
|Status|String|Filter by account status|||`provisioned`<BR>`operational`|||
|IsHorizonAcct|String|Restrict results to Falcon Horizon|||`false`<BR>`true`|||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconContainerAwsAccount [[-Id] <String[]>] [[-Status] <String>] [[-IsHorizonAcct] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/accounts/aws/v1
```
### falconpy
[GetAWSAccountsMixin0](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetAWSAccountsMixin0)
## USAGE
### List AWS account details
```powershell
Get-FalconContainerAwsAccount -Detailed
```

_2023-11-27: PSFalcon v2.2.6_
