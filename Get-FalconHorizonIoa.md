# Get-FalconHorizonIoa
## SYNOPSIS
Search for Falcon Horizon Indicators of Attack
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|CloudPlatform|String|Cloud platform|||`aws`<BR>`azure`|||
|AccountId|String|Cloud account identifier|||||X|
|AwsAccountId|String|AWS account identifier|||||X|
|AzureSubscriptionId|String|Azure subscription identifier|||||X|
|AzureTenantId|String|Azure tenant identifier|||||X|
|ResourceId|String[]|Resource identifier||||||
|ResourceUuid|String[]|Resource UUID||||||
|Severity|String|Indicator of Attack severity|||`High`<BR>`Medium`<BR>`Informational`|||
|Service|String|Cloud service|||`ACM`<BR>`ACR`<BR>`Any`<BR>`App Engine`<BR>`AppService`<BR>`BigQuery`<BR>`Cloud Load Balancing`<BR>`Cloud Logging`<BR>`Cloud SQL`<BR>`Cloud Storage`<BR>`CloudFormation`<BR>`CloudTrail`<BR>`CloudWatch Logs`<BR>`Cloudfront`<BR>`Compute Engine`<BR>`Config`<BR>`Disk`<BR>`DynamoDB`<BR>`EBS`<BR>`EC2`<BR>`ECR`<BR>`EFS`<BR>`EKS`<BR>`ELB`<BR>`EMR`<BR>`Elasticache`<BR>`GuardDuty`<BR>`IAM`<BR>`Identity`<BR>`KMS`<BR>`KeyVault`<BR>`Kinesis`<BR>`Kubernetes`<BR>`Lambda`<BR>`LoadBalancer`<BR>`Monitor`<BR>`NLB/ALB`<BR>`NetworkSecurityGroup`<BR>`PostgreSQL`<BR>`RDS`<BR>`Redshift`<BR>`S3`<BR>`SES`<BR>`SNS`<BR>`SQLDatabase`<BR>`SQLServer`<BR>`SQS`<BR>`SSM`<BR>`Serverless Application Repository`<BR>`StorageAccount`<BR>`Subscriptions`<BR>`VPC`<BR>`VirtualMachine`<BR>`VirtualNetwork`|||
|State|String|Indicator of Attack state|||`open`<BR>`closed`|||
|Since|String|Filter events using a duration string (e.g. 24h)||||||
|DateTimeSince|String|Include results that occur after a specific date and time (RFC3339)||||||
|Limit|Int32|Maximum number of results per request|`1`|`1000`||||
|NextToken|String|Pagination token to retrieve the next set of results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHorizonIoa [-CloudPlatform] <String> [[-AccountId] <String>] [[-AwsAccountId] <String>] [[-AzureSubscriptionId] <String>] [[-AzureTenantId] <String>] [[-ResourceId] <String[]>] [[-ResourceUuid] <String[]>] [[-Severity] <String>] [[-Service] <String>] [[-State] <String>] [[-Since] <String>] [[-DateTimeSince] <String>] [[-Limit] <Int32>] [-NextToken <String>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /detects/entities/ioa/v1
```
### falconpy
[GetBehaviorDetections](https://github.com/CrowdStrike/falconpy/wiki/detects#GetBehaviorDetections)
## USAGE
### List information about IOAs
```powershell
Get-FalconHorizonIoa [-Detailed] [-All]
```

_2023-11-27: PSFalcon v2.2.6_
