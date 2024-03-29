# New-FalconDiscoverAzureAccount
## SYNOPSIS
Provision Falcon Discover for Cloud Azure accounts
## DESCRIPTION
Requires 'D4C registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SubscriptionId|String|Azure subscription identifier|||||X|
|TenantId|String|Azure tenant identifier|||||X|
## SYNTAX
```powershell
New-FalconDiscoverAzureAccount [[-SubscriptionId] <String>] [[-TenantId] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /cloud-connect-azure/entities/account/v1
```
### falconpy
[CreateDiscoverCloudAzureAccount](https://github.com/CrowdStrike/falconpy/wiki/d4c-registration#CreateDiscoverCloudAzureAccount)
## USAGE
### Enable Discover for Cloud and Containers with Subscription and Tenant IDs
```powershell
New-FalconDiscoverAzureAccount -SubscriptionId <id> -TenantId <id>
```
_See [Receive-FalconDiscoverAzureScript](Receive-FalconDiscoverAzureScript)_.

_2023-04-25: PSFalcon v2.2.5_
