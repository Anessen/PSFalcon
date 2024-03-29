# Get-FalconHorizonPolicy
## SYNOPSIS
Retrieve detailed information about Falcon Horizon policies
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|Int32[]|Policy identifier||||X|X|
|PolicyId|Int32|Policy identifier||||||
|Service|String|Cloud service type|||`ACM`<BR>`ACR`<BR>`Any`<BR>`App Engine`<BR>`AppService`<BR>`BigQuery`<BR>`Cloud Load Balancing`<BR>`Cloud Logging`<BR>`Cloud SQL`<BR>`Cloud Storage`<BR>`CloudFormation`<BR>`CloudTrail`<BR>`CloudWatch Logs`<BR>`Cloudfront`<BR>`Compute Engine`<BR>`Config`<BR>`Disk`<BR>`DynamoDB`<BR>`EBS`<BR>`EC2`<BR>`ECR`<BR>`EFS`<BR>`EKS`<BR>`ELB`<BR>`EMR`<BR>`Elasticache`<BR>`GuardDuty`<BR>`IAM`<BR>`Identity`<BR>`KMS`<BR>`KeyVault`<BR>`Kinesis`<BR>`Kubernetes`<BR>`Lambda`<BR>`LoadBalancer`<BR>`Monitor`<BR>`NLB/ALB`<BR>`NetworkSecurityGroup`<BR>`PostgreSQL`<BR>`RDS`<BR>`Redshift`<BR>`S3`<BR>`SES`<BR>`SNS`<BR>`SQLDatabase`<BR>`SQLServer`<BR>`SQS`<BR>`SSM`<BR>`Serverless Application Repository`<BR>`StorageAccount`<BR>`Subscriptions`<BR>`VPC`<BR>`VirtualMachine`<BR>`VirtualNetwork`|||
|CloudPlatform|String|Cloud platform|||`aws`<BR>`azure`<BR>`gcp`|||
## SYNTAX
```powershell
Get-FalconHorizonPolicy [[-PolicyId] <Int32>] [[-Service] <String>] [[-CloudPlatform] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHorizonPolicy -Id <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /settings/entities/policy/v1
GET /settings/entities/policy-details/v2
```
### falconpy
[GetCSPMPolicySettings](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMPolicySettings)<BR>[GetCSPMPoliciesDetails](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMPoliciesDetails)
## USAGE
### Retrieve a policy
```powershell
Get-FalconHorizonPolicy -Id <id>, <id>
```
### Retrieving policies by service
```powershell
Get-FalconHorizonPolicy -Service <service_name> [-Detailed]
```

_2023-04-25: PSFalcon v2.2.5_
