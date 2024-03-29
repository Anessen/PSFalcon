# Remove-FalconDiscoverAwsAccount
## SYNOPSIS
Remove Falcon Discover for Cloud AWS accounts
## DESCRIPTION
Requires 'AWS accounts: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|OrganizationId|String[]|AWS organization identifier||||X|X|
|Id|String[]|AWS account identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconDiscoverAwsAccount [-OrganizationId] <String[]> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /cloud-connect-aws/entities/account/v2
```
### falconpy
[DeleteD4CAwsAccount](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#DeleteD4CAwsAccount)
## USAGE
### Delete AWS accounts
```powershell
Remove-FalconDiscoverAwsAccount -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
