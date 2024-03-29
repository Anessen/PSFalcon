# Get-FalconDetection
## SYNOPSIS
Search for detections
## DESCRIPTION
Requires 'Detections: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Detection identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`behaviors.parent_details.parent_md5`<BR>`behaviors.parent_details.parent_process_graph_id`<BR>`behaviors.parent_details.parent_cmdline`<BR>`behaviors.parent_details.parent_sha256`<BR>`behaviors.parent_details.parent_process_id`<BR>`behaviors.confidence`<BR>`behaviors.severity`<BR>`behaviors.triggering_process_id`<BR>`behaviors.filename`<BR>`behaviors.sha256`<BR>`behaviors.user_name`<BR>`behaviors.user_id`<BR>`behaviors.behavior_id`<BR>`behaviors.timestamp`<BR>`behaviors.alle`<BR>`behaviors.objective`<BR>`behaviors.tactic`<BR>`behaviors.technique`<BR>`behaviors.pattern_disposition`<BR>`behaviors.cmdline`<BR>`behaviors.triggering_process_graph_id`<BR>`behaviors.ioc_type`<BR>`behaviors.ioc_source`<BR>`behaviors.ioc_value`<BR>`behaviors.device_id`<BR>`device.first_seen`<BR>`device.last_seen`<BR>`device.modified_timestamp`<BR>`device.site_name`<BR>`device.config_id_platform`<BR>`device.system_manufacturer`<BR>`device.bios_manufacturer`<BR>`device.platform_name`<BR>`device.hostname`<BR>`device.config_id_build`<BR>`device.os_version`<BR>`device.bios_version`<BR>`device.agent_load_flags`<BR>`device.release_group`<BR>`device.status`<BR>`device.product_type_desc`<BR>`device.machine_domain`<BR>`device.agent_local_time`<BR>`device.device_id`<BR>`device.system_product_name`<BR>`device.product_type`<BR>`device.cid`<BR>`device.external_ip`<BR>`device.major_version`<BR>`device.minor_version`<BR>`device.platform_id`<BR>`device.config_id_base`<BR>`device.ou`<BR>`device.agent_version`<BR>`device.local_ip`<BR>`device.mac_address`<BR>`device.cpu_signature`<BR>`device.reduced_functionality_mode`<BR>`device.serial_number`<BR>`hostinfo.domain`<BR>`hostinfo.active_directory_dn_display`<BR>`quarantined_files.paths`<BR>`quarantined_files.state`<BR>`quarantined_files.sha256`<BR>`quarantined_files.id`<BR>`q`<BR>`date_updated`<BR>`assigned_to_name`<BR>`max_confidence`<BR>`detection_id`<BR>`max_severity`<BR>`max_severity_displayname`<BR>`seconds_to_triaged`<BR>`seconds_to_resolved`<BR>`status`<BR>`adversary_ids`<BR>`cid`<BR>`first_behavior`<BR>`last_behavior`||||||
|Query|String|Perform a generic substring search across available fields||||||
|Sort|String|Property and direction to sort results|||`adversary_id.asc`<BR>`adversary_id.desc`<BR>`devices.hostname.asc`<BR>`devices.hostname.desc`<BR>`first_behavior.asc`<BR>`first_behavior.desc`<BR>`last_behavior.asc`<BR>`last_behavior.desc`<BR>`max_confidence.asc`<BR>`max_confidence.desc`<BR>`max_severity.asc`<BR>`max_severity.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconDetection [[-Filter] <String>] [[-Query] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconDetection -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /detects/queries/detects/v1
POST /detects/entities/summaries/GET/v1
```
### falconpy
[QueryDetects](https://github.com/CrowdStrike/falconpy/wiki/detects#QueryDetects)<BR>[GetDetectSummaries](https://github.com/CrowdStrike/falconpy/wiki/detects#GetDetectSummaries)
## USAGE
### Find detections
```powershell
Get-FalconDetection -Filter "status:'new'+first_behavior:>'2020-01-01'" -Sort first_behavior.desc [-Detailed] [-All]
```
### Find unassigned detections
```powershell
Get-FalconDetection -Filter "assigned_to_uid:null" [-All]
```

_2023-04-25: PSFalcon v2.2.5_
