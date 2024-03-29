# Receive-FalconHorizonAwsScript
## SYNOPSIS
Download a Bash script which grants Falcon Horizon access using the AWS CLI
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|AWS account identifier||||X|X|
|Path|String|Destination path||||||
|Force|Switch|Overwrite existing file when present||||||
## SYNTAX
```powershell
Receive-FalconHorizonAwsScript [[-Id] <String[]>] [-Path] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-cspm-aws/entities/user-scripts-download/v1
```
### falconpy
[GetCSPMAwsAccountScriptsAttachment](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMAwsAccountScriptsAttachment)
## USAGE
### Generate an AWS Cloudformation script
```powershell
Receive-FalconHorizonAwsScript -Path .\aws_provision.sh
```
**NOTE**: The script must be run using [AWS CLI Version 2](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html).

_2023-11-27: PSFalcon v2.2.6_
