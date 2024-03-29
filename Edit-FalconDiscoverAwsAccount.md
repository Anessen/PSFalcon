# Edit-FalconDiscoverAwsAccount
## SYNOPSIS
Modify a Falcon Discover for Cloud AWS account
## DESCRIPTION
Requires 'AWS accounts: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ExternalId|String|AWS account identifier with cross-account IAM role access|||||X|
|IamRoleArn|String|Full ARN of the IAM role created in the AWS account to control access|||||X|
|CloudtrailBucketOwnerId|String|AWS account identifier containing cloudtrail logs|||||X|
|CloudtrailBucketRegion|String|AWS region where the account containing cloudtrail logs resides|||||X|
|RateLimitTime|Int64|Number of seconds between requests defined by 'RateLimitReq'|||||X|
|RateLimitReq|Int32|Maximum number of requests within 'RateLimitTime'|||||X|
|Id|String|AWS account identifier|||||X|
## SYNTAX
```powershell
Edit-FalconDiscoverAwsAccount [[-ExternalId] <String>] [[-IamRoleArn] <String>] [[-CloudtrailBucketOwnerId] <String>] [[-CloudtrailBucketRegion] <String>] [[-RateLimitTime] <Int64>] [[-RateLimitReq] <Int32>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /cloud-connect-aws/entities/accounts/v1
```
### falconpy
[UpdateAWSAccounts](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#UpdateAWSAccounts)
## USAGE
### Update AWS accounts
```powershell
Edit-FalconDiscoverAwsAccount -Id <id> -ExternalId 'fsdfk230fsdk' -CloudtrailBucketOwnerId '222222222222'
```

_2023-04-25: PSFalcon v2.2.5_
