# Remove-FalconHorizonAzureAccount
## SYNOPSIS
Remove Falcon Horizon Azure accounts
## DESCRIPTION
Requires 'CSPM registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|TenantId|String[]|Azure tenant identifier||||||
|RetainTenant|Boolean|Retain Azure tenant when removing an account||||||
|Id|String[]|Azure account identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconHorizonAzureAccount [[-TenantId] <String[]>] [[-RetainTenant] <Boolean>] -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /cloud-connect-cspm-azure/entities/account/v1
```
### falconpy
[DeleteCSPMAzureAccount](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#DeleteCSPMAzureAccount)
## USAGE
### Deprovision an Azure account
```powershell
Remove-FalconHorizonAzureAccount -Id <id>, <id>
```

_2023-11-27: PSFalcon v2.2.6_
