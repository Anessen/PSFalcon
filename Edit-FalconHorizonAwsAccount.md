# Edit-FalconHorizonAwsAccount
## SYNOPSIS
Modify a Falcon Horizon AWS account
## DESCRIPTION
Requires 'CSPM registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|AccountId|String|AWS account identifier|||||X|
|CloudtrailRegion|String|AWS region where the account resides|||`af-south-1`<BR>`ap-east-1`<BR>`ap-northeast-1`<BR>`ap-northeast-2`<BR>`ap-northeast-3`<BR>`ap-south-1`<BR>`ap-south-2`<BR>`ap-southeast-1`<BR>`ap-southeast-2`<BR>`ap-southeast-3`<BR>`ap-southeast-4`<BR>`ca-central-1`<BR>`cn-north-1`<BR>`cn-northwest-1`<BR>`eu-central-1`<BR>`eu-central-2`<BR>`eu-north-1`<BR>`eu-south-1`<BR>`eu-south-2`<BR>`eu-west-1`<BR>`eu-west-2`<BR>`eu-west-3`<BR>`il-central-1`<BR>`me-central-1`<BR>`me-south-1`<BR>`sa-east-1`<BR>`us-east-1`<BR>`us-east-2`<BR>`us-gov-east-1`<BR>`us-gov-west-1`<BR>`us-west-1`<BR>`us-west-2`||X|
|IamRoleArn|String|AWS IAM role ARNs|||||X|
|BehaviorAssessmentEnabled|Boolean|Enable behavior assessment for account|||||X|
|SensorManagementEnabled|Boolean|Enable sensor management for account|||||X|
|RemediationRegion|String|Region where remediation occurs|||||X|
|RemediationTouAccepted|String|Remediation terms-of-use acceptance date|||||X|
## SYNTAX
```powershell
Edit-FalconHorizonAwsAccount [-AccountId] <String> [[-CloudtrailRegion] <String>] [[-IamRoleArn] <String>] [[-BehaviorAssessmentEnabled] <Boolean>] [[-SensorManagementEnabled] <Boolean>] [[-RemediationRegion] <String>] [[-RemediationTouAccepted] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /cloud-connect-cspm-aws/entities/account/v1
```
### falconpy
[PatchCSPMAwsAccount](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#PatchCSPMAwsAccount)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
