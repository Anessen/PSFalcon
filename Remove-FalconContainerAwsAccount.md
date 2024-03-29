# Remove-FalconContainerAwsAccount
## SYNOPSIS
Remove Falcon Container Security AWS accounts
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|AWS account identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconContainerAwsAccount [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /kubernetes-protection/entities/accounts/aws/v1
```
### falconpy
[DeleteAWSAccountsMixin0](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#DeleteAWSAccountsMixin0)
## USAGE
### Remove AWS accounts
```powershell
Remove-FalconContainerAwsAccount -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
