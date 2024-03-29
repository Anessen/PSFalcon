# Get-FalconHorizonIoaEvent
## SYNOPSIS
Retrieve Falcon Horizon Indicator of Attack events
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
|UserId|String[]|User identifier||||||
|State|String|Event state||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHorizonIoaEvent [-PolicyId] <Int32> [[-CloudPlatform] <String>] [[-AwsAccountId] <String>] [[-AzureSubscriptionId] <String>] [[-AzureTenantId] <String>] [[-UserId] <String[]>] [[-State] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /ioa/entities/events/v1
```
### falconpy
[GetIOAEvents](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetIOAEvents)
## USAGE
### Retrieve events using a filtered search
```powershell
Get-FalconHorizonIoaEvent -Filter "cloud_provider:'aws'" [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
