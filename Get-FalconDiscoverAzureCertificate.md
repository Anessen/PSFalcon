# Get-FalconDiscoverAzureCertificate
## SYNOPSIS
Retrieve the base64 encoded certificate for a Falcon Discover Azure tenant
## DESCRIPTION
Requires 'D4C registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Refresh|Boolean|Refresh certificate [default: false]||||||
|TenantId|String[]|Azure tenant identifier||||X|X|
## SYNTAX
```powershell
Get-FalconDiscoverAzureCertificate [[-Refresh] <Boolean>] [-TenantId] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-azure/entities/download-certificate/v1
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
