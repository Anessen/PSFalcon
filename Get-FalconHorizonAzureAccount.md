# Get-FalconHorizonAzureAccount
## SYNOPSIS
Search for Falcon Horizon Azure accounts
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Azure subscription identifier||||||
|TenantId|String[]|Azure tenant identifier||||||
|ScanType|String|Scan type|||`full`<BR>`dry`|||
|Status|String|Azure account status|||`provisioned`<BR>`operational`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHorizonAzureAccount [[-Id] <String[]>] [[-TenantId] <String[]>] [[-ScanType] <String>] [[-Status] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-cspm-azure/entities/account/v1
```
### falconpy
[GetCSPMAzureAccount](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMAzureAccount)
## USAGE
### Check that the Azure account was correctly provisioned
```powershell
Get-FalconHorizonAzureAccount -Id <id>
```
A properly provisioned account will display status: `Event_DiscoverAccountStatusOperational`.

_2023-11-27: PSFalcon v2.2.6_
