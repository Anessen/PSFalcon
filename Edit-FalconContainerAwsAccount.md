# Edit-FalconContainerAwsAccount
## SYNOPSIS
Modify Falcon Container Security AWS accounts
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Region|String|AWS cloud region||||||
|Id|String[]|AWS account identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconContainerAwsAccount [[-Region] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /kubernetes-protection/entities/accounts/aws/v1
```
### falconpy
[UpdateAWSAccount](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#UpdateAWSAccount)
## USAGE
### Update existing AWS accounts
```powershell
Edit-FalconContainerAwsAccount -Id <id>, <id> -Region <string>
```

_2023-04-25: PSFalcon v2.2.5_
