# Receive-FalconHorizonAzureScript
## SYNOPSIS
Download a Bash script which grants Falcon Horizon access using Azure Cloud Shell
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|TenantId|String|Azure tenant identifier [default: most recently registered]||||X|X|
|SubscriptionId|String[]|Azure subscription identifier [default: all]||||||
|Template|String|Template to be rendered||||||
|AccountType|String|Account type|||`commercial`<BR>`gov`|||
|Path|String|Destination path||||||
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconHorizonAzureScript [[-TenantId] <String>] [[-SubscriptionId] <String[]>] [[-Template] <String>] [[-AccountType] <String>] [-Path] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-cspm-azure/entities/user-scripts-download/v1
```
### falconpy
[GetCSPMAzureUserScriptsAttachment](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMAzureUserScriptsAttachment)
## USAGE
### Generate an Azure CLI script
```powershell
Receive-FalconHorizonAzureScript -TenantId <id> -Path .\azure_provision.sh
```
**NOTE**: This script needs to be executed within your Azure Cloud Shell (Bash).

_2023-11-27: PSFalcon v2.2.6_
