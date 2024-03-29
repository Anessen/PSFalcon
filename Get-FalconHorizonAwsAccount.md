# Get-FalconHorizonAwsAccount
## SYNOPSIS
Search for Falcon Horizon AWS accounts
## DESCRIPTION
A properly provisioned AWS account will display the status 'Event_DiscoverAccountStatusOperational'.

Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|AWS account identifier||||X|X|
|OrganizationId|String[]|AWS organization identifier||||||
|ScanType|String|Scan type|||`full`<BR>`dry`|||
|Status|String|AWS account status|||`provisioned`<BR>`operational`|||
|GroupBy|String|Field to group by|||`organization`|||
|IamRoleArn|String[]|AWS IAM role ARNs||||||
|Migrated|Boolean|Only return migrated Discover for Cloud accounts||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHorizonAwsAccount [-Id <String[]>] [[-OrganizationId] <String[]>] [[-ScanType] <String>] [[-Status] <String>] [[-GroupBy] <String>] [[-IamRoleArn] <String[]>] [[-Migrated] <Boolean>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-cspm-aws/entities/account/v1
```
### falconpy
[GetCSPMAwsAccount](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMAwsAccount)
## USAGE
### Check that the AWS account was correctly provisioned
```powershell
Get-FalconHorizonAwsAccount -Id <id>
```
A properly provisioned account will display status: `Event_DiscoverAccountStatusOperational`.

_2023-11-27: PSFalcon v2.2.6_
