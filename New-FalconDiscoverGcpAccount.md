# New-FalconDiscoverGcpAccount
## SYNOPSIS
Provision Falcon Discover for Cloud GCP accounts
## DESCRIPTION
Requires 'D4C registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ParentId|String|GCP project identifier||||X|X|
## SYNTAX
```powershell
New-FalconDiscoverGcpAccount [-ParentId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /cloud-connect-gcp/entities/account/v1
```
### falconpy
[CreateD4CGCPAccount](https://github.com/CrowdStrike/falconpy/wiki/d4c-registration#CreateD4CGCPAccount)
## USAGE
### Enable Discover for Cloud and Containers with Parent ID
```powershell
New-FalconDiscoverGcpAccount -ParentId <id>
```
_See [Receive-FalconDiscoverGcpScript](Receive-FalconDiscoverGcpScript)_.

_2023-04-25: PSFalcon v2.2.5_
