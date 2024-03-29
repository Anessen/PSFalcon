# Confirm-FalconDiscoverAwsAccess
## SYNOPSIS
Verify Falcon Discover for Cloud AWS account access
## DESCRIPTION
Requires 'AWS accounts: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|AWS account identifier||||X|X|
## SYNTAX
```powershell
Confirm-FalconDiscoverAwsAccess [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /cloud-connect-aws/entities/verify-account-access/v1
```
### falconpy
[VerifyAWSAccountAccess](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#VerifyAWSAccountAccess)
## USAGE
### Verify access to provisioned AWS accounts
```powershell
Confirm-FalconDiscoverAwsAccess -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
