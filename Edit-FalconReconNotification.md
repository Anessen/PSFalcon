# Edit-FalconReconNotification
## SYNOPSIS
Modify a Falcon Intelligence Recon notification
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of notifications to modify in a single request||||X||
|Id|String|Notification identifier||||||
|Status|String|Notification status|||`new`<BR>`in-progress`<BR>`closed-false-positive`<BR>`closed-true-positive`|||
|AssignedToUuid|String|User identifier||||||
|Message|String|||||||
|IdpSendStatus|String|||||||
## SYNTAX
```powershell
Edit-FalconReconNotification [-Id] <String> [-Status] <String> [-AssignedToUuid] <String> [[-Message] <String>] [[-IdpSendStatus] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconReconNotification -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /recon/entities/notifications/v1
```
### falconpy
[UpdateNotificationsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#UpdateNotificationsV1)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
