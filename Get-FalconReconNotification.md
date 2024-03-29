# Get-FalconReconNotification
## SYNOPSIS
Search for Falcon Intelligence Recon notifications
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Notification identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`created_date\|asc`<BR>`created_date\|desc`<BR>`updated_date\|asc`<BR>`updated_date\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
|Intel|Switch|Include raw intelligence content||||||
|Translate|Switch|Translate to English||||||
|Combined|Switch|Include raw intelligence content and translate to English||||||
## SYNTAX
```powershell
Get-FalconReconNotification [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReconNotification -Id <String[]> -Combined [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReconNotification -Id <String[]> -Translate [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReconNotification -Id <String[]> -Intel [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReconNotification -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /recon/entities/notifications/v1
GET /recon/entities/notifications-detailed/v1
GET /recon/entities/notifications-detailed-translated/v1
GET /recon/entities/notifications-translated/v1
GET /recon/queries/notifications/v1
```
### falconpy
[QueryNotificationsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#QueryNotificationsV1)<BR>[GetNotificationsDetailedTranslatedV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetNotificationsDetailedTranslatedV1)<BR>[GetNotificationsTranslatedV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetNotificationsTranslatedV1)<BR>[GetNotificationsDetailedV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetNotificationsDetailedV1)<BR>[GetNotificationsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetNotificationsV1)
## USAGE
### Querying notifications
```powershell
Get-FalconReconNotification
```
### Get simplified data from notifications
```powershell
Get-FalconReconNotification [-Detailed]
```
### Get raw intelligence data from notifications
```powershell
Get-FalconReconNotification -Id <id>, <id> -Intel
```
### Get data from notifications translated into English
```powershell
Get-FalconReconNotification -Id <id>, <id> -Translate
```
### Get raw intelligence data from notifications translated into English
```powershell
Get-FalconReconNotification -Id <id>, <id> -Combined
```

_2023-04-25: PSFalcon v2.2.5_
