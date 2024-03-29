# New-FalconHorizonAzureAccount
## SYNOPSIS
Provision a Falcon Horizon Azure account
## DESCRIPTION
Requires 'CSPM registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SubscriptionId|String|Azure subscription identifier|||||X|
|TenantId|String|Azure tenant identifier|||||X|
|ClientId|String|Azure client identifier||||||
|AccountType|String|Azure account type||||||
|DefaultSubscription|Boolean|Account is the default Azure subscription||||||
|YearsValid|Int32|Number of years valid||||||
## SYNTAX
```powershell
New-FalconHorizonAzureAccount [[-SubscriptionId] <String>] [[-TenantId] <String>] [[-ClientId] <String>] [[-AccountType] <String>] [[-DefaultSubscription] <Boolean>] [[-YearsValid] <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /cloud-connect-cspm-azure/entities/account/v1
```
### falconpy
[CreateCSPMAzureAccount](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#CreateCSPMAzureAccount)
## USAGE
### Register an Azure account
```powershell
New-FalconHorizonAzureAccount -SubscriptionId <id> -TenantId <id>
```

_2023-11-27: PSFalcon v2.2.6_
