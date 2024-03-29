# Get-FalconDiscoverAzureAccount
## SYNOPSIS
Search for Falcon Discover for Cloud Azure accounts
## DESCRIPTION
Requires 'D4C registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ScanType|String|Scan type|||`full`<BR>`dry`|||
|Id|String[]|Azure account identifier||||X|X|
## SYNTAX
```powershell
Get-FalconDiscoverAzureAccount [[-ScanType] <String>] [[-Id] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-azure/entities/account/v1
```
### falconpy
[GetDiscoverCloudAzureAccount](https://github.com/CrowdStrike/falconpy/wiki/d4c-registration#GetDiscoverCloudAzureAccount)
## USAGE
### Validate provisioning status
```powershell
Get-FalconDiscoverAzureAccount -Id <id> -ScanType dry
```
A properly provisioned account will display status: `Event_DiscoverAccountStatusOperational`.

_2023-04-25: PSFalcon v2.2.5_
