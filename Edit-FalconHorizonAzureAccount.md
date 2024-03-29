# Edit-FalconHorizonAzureAccount
## SYNOPSIS
Modify the default Falcon Horizon Azure client or subscription identifier
## DESCRIPTION
Requires 'CSPM registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Azure client identifier|||||X|
|SubscriptionId|String|Azure subscription identifier|||||X|
|TenantId|String|Azure tenant identifier, required when multiple tenants have been registered|||||X|
## SYNTAX
```powershell
Edit-FalconHorizonAzureAccount [-Id] <String> [[-TenantId] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconHorizonAzureAccount -SubscriptionId <String> [[-TenantId] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /cloud-connect-cspm-azure/entities/client-id/v1
PATCH /cloud-connect-cspm-azure/entities/default-subscription-id/v1
```
### falconpy
[UpdateCSPMAzureAccountClientID](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#UpdateCSPMAzureAccountClientID)<BR>[UpdateCSPMAzureTenantDefaultSubscriptionID](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#UpdateCSPMAzureTenantDefaultSubscriptionID)
## USAGE
### Update an Azure account
```powershell
Edit-FalconHorizonAzureAccount -Id <id> [-TenantId <id>]
```

_2023-04-25: PSFalcon v2.2.5_
