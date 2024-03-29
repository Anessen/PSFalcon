# Get-FalconHorizonIom
## SYNOPSIS
Search for Falcon Horizon Indicators of Misconfiguration
## DESCRIPTION
Requires 'CSPM registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Horizon Indicator of Misconfiguration identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`account_id`<BR>`account_name`<BR>`agent_id`<BR>`attack_types`<BR>`azure_subscription_id`<BR>`cloud_provider`<BR>`cloud_service_keyword`<BR>`custom_policy_id`<BR>`is_managed`<BR>`policy_id`<BR>`policy_type`<BR>`region`<BR>`resource_id`<BR>`scan_time`<BR>`severity`<BR>`severity_string`<BR>`status`<BR>`use_current_scan_ids`||||||
|Sort|String|Property and direction to sort results|||`account_name.asc`<BR>`account_name.desc`<BR>`account_id.asc`<BR>`account_id.desc`<BR>`attack_types.asc`<BR>`attack_types.desc`<BR>`azure_subscription_id.asc`<BR>`azure_subscription_id.desc`<BR>`cloud_provider.asc`<BR>`cloud_provider.desc`<BR>`cloud_service_keyword.asc`<BR>`cloud_service_keyword.desc`<BR>`status.asc`<BR>`status.desc`<BR>`is_managed.asc`<BR>`is_managed.desc`<BR>`policy_id.asc`<BR>`policy_id.desc`<BR>`policy_type.asc`<BR>`policy_type.desc`<BR>`resource_id.asc`<BR>`resource_id.desc`<BR>`region.asc`<BR>`region.desc`<BR>`scan_time.asc`<BR>`scan_time.desc`<BR>`severity.asc`<BR>`severity.desc`<BR>`severity_string.asc`<BR>`severity_string.desc`<BR>`timestamp.asc`<BR>`timestamp.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`1000`||||
|Offset|Int32|Position to begin retrieving results||||||
|NextToken|String|Pagination token to retrieve the next set of results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHorizonIom [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-NextToken <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHorizonIom -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /detects/entities/iom/v2
GET /detects/queries/iom/v2
```
### falconpy
[GetConfigurationDetectionIDsV2](https://github.com/CrowdStrike/falconpy/wiki/detects#GetConfigurationDetectionIDsV2)<BR>[GetConfigurationDetectionEntities](https://github.com/CrowdStrike/falconpy/wiki/detects#GetConfigurationDetectionEntities)
## USAGE
### Retrieve events using a filtered search
```powershell
Get-FalconHorizonIom -Filter "cloud_provider:'azure'+region:'eastus'+severity=1" [-Detailed] [-All]
```

_2023-11-27: PSFalcon v2.2.6_
