# Get-FalconDiscoverGcpAccount
## SYNOPSIS
Search for Falcon Discover for Cloud GCP accounts
## DESCRIPTION
Requires 'D4C registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ScanType|String|Scan type|||`full`<BR>`dry`|||
|Id|String[]|GCP account identifier||||X|X|
## SYNTAX
```powershell
Get-FalconDiscoverGcpAccount [[-ScanType] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-gcp/entities/account/v1
```
### falconpy
[GetD4CCGPAccount](https://github.com/CrowdStrike/falconpy/wiki/d4c-registration#GetD4CCGPAccount)
## USAGE
### Validate provisioning status
```powershell
Get-FalconDiscoverGcpAccount -Id <id> -ScanType dry
```
A properly provisioned account will display status: `Event_DiscoverAccountStatusOperational`.

_2023-04-25: PSFalcon v2.2.5_
