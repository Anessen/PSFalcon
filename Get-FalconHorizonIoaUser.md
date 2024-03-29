# Get-FalconHorizonIoaUser
## SYNOPSIS
Retrieve Falcon Horizon Indicator of Attack users
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PolicyId|Int32|Policy identifier|||||X|
|CloudPlatform|String|Cloud platform|||`aws`<BR>`azure`<BR>`gcp`|||
|AwsAccountId|String|AWS account identifier|||||X|
|AzureSubscriptionId|String|Azure subscription identifier|||||X|
|AzureTenantId|String|Azure tenant identifier|||||X|
|State|String|Event state||||||
## SYNTAX
```powershell
Get-FalconHorizonIoaUser [-PolicyId] <Int32> [[-CloudPlatform] <String>] [[-AwsAccountId] <String>] [[-AzureSubscriptionId] <String>] [[-AzureTenantId] <String>] [[-State] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ioa/entities/users/v1
```
### falconpy
[GetIOAUsers](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetIOAUsers)
## USAGE
### Find users associated with an IOA
```powershell
Get-FalconHorizonIoaUser -PolicyId <id> -CloudPlatform aws
```

_2023-04-25: PSFalcon v2.2.5_
