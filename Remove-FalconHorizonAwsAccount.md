# Remove-FalconHorizonAwsAccount
## SYNOPSIS
Remove Falcon Horizon AWS accounts
## DESCRIPTION
Requires 'CSPM registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|AWS account identifier||||X|X|
|OrganizationId|String[]|AWS organization identifier||||||
## SYNTAX
```powershell
Remove-FalconHorizonAwsAccount [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Remove-FalconHorizonAwsAccount -OrganizationId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /cloud-connect-cspm-aws/entities/account/v1
```
### falconpy
[DeleteCSPMAwsAccount](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#DeleteCSPMAwsAccount)
## USAGE
### Deprovision an AWS account
```powershell
Remove-FalconHorizonAwsAccount -Id <id>
```
### Deprovision an AWS organization
```powershell
Remove-FalconHorizonAwsAccount -OrganizationId <id>
```

_2023-04-25: PSFalcon v2.2.5_
