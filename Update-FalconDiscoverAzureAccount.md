# Update-FalconDiscoverAzureAccount
## SYNOPSIS
Update the Azure Service Principal for Falcon Discover for Cloud
## DESCRIPTION
Requires 'D4C registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Azure client identifier for the associated Service Principal||||X|X|
## SYNTAX
```powershell
Update-FalconDiscoverAzureAccount [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /cloud-connect-azure/entities/client-id/v1
```
### falconpy
[UpdateDiscoverCloudAzureAccountClientID](https://github.com/CrowdStrike/falconpy/wiki/d4c-registration#UpdateDiscoverCloudAzureAccountClientID)
## USAGE
### Update Azure service account
```powershell
Update-FalconDiscoverAzureAccount -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
