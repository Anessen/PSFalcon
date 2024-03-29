# Remove-FalconReconNotification
## SYNOPSIS
Remove Falcon Intelligence Recon notifications
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Notification identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconReconNotification [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /recon/entities/notifications/v1
```
### falconpy
[DeleteNotificationsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#DeleteNotificationsV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
