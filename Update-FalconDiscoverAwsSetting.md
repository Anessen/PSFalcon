# Update-FalconDiscoverAwsSetting
## SYNOPSIS
Create or update global settings applicable to all newly-provisioned Falcon Discover for Cloud AWS accounts
## DESCRIPTION
Requires 'AWS accounts: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|CloudtrailBucketOwnerId|String|AWS account identifier containing cloudtrail logs|||||X|
|StaticExternalId|String|Default external identifier to apply to AWS accounts|||||X|
## SYNTAX
```powershell
Update-FalconDiscoverAwsSetting [[-CloudtrailBucketOwnerId] <String>] [[-StaticExternalId] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /cloud-connect-aws/entities/settings/v1
```
### falconpy
[CreateOrUpdateAWSSettings](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#CreateOrUpdateAWSSettings)
## USAGE
### Set and update global settings
```powershell
Update-FalconDiscoverAwsSetting -CloudTrailBucketOwnerId <id>
```

_2023-04-25: PSFalcon v2.2.5_
