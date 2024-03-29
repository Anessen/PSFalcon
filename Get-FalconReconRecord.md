# Get-FalconReconRecord
## SYNOPSIS
Search for Falcon Intelligence Recon exposed data record notifications
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Exposed data record identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request||||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconReconRecord [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconReconRecord -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /recon/entities/notifications-exposed-data-records/v1
GET /recon/queries/notifications-exposed-data-records/v1
```
### falconpy
[QueryNotificationsExposedDataRecordsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#QueryNotificationsExposedDataRecordsV1)<BR>[GetNotificationsExposedDataRecordsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#GetNotificationsExposedDataRecordsV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
