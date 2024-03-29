# Get-FalconHorizonAzureCertificate
## SYNOPSIS
Retrieve the base64 encoded certificate for a Falcon Horizon Azure tenant
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Refresh|Boolean|Refresh certificate [default: false]||||||
|YearsValid|String|Years the certificate should be valid [when Refresh: true]||||||
|TenantId|String[]|Azure tenant identifier||||X|X|
## SYNTAX
```powershell
Get-FalconHorizonAzureCertificate [[-Refresh] <Boolean>] [[-YearsValid] <String>] [-TenantId] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-cspm-azure/entities/download-certificate/v1
```
### falconpy
[AzureDownloadCertificate](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#AzureDownloadCertificate)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
