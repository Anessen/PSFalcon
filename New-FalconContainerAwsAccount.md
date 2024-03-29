# New-FalconContainerAwsAccount
## SYNOPSIS
Provision Falcon Container Security AWS accounts
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Region|String|AWS cloud region||||||
|Id|String|AWS account identifier||||X|X|
## SYNTAX
```powershell
New-FalconContainerAwsAccount [-Region] <String> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /kubernetes-protection/entities/accounts/aws/v1
```
### falconpy
[CreateAWSAccount](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#CreateAWSAccount)
## USAGE
### Create a new AWS account and generate installation script
```powershell
New-FalconContainerAwsAccount -Id <id> -Region <string>
```

_2023-04-25: PSFalcon v2.2.5_
