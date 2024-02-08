# Get-FalconAsset
## SYNOPSIS
Search for assets in Falcon Discover
## DESCRIPTION
Requires 'Falcon Discover: Read' and 'Falcon Discover IoT: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Asset identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`account_enabled`<BR>`ad_user_account_control`<BR>`agent_version`<BR>`aid`<BR>`assigned_to`<BR>`bios_manufacturer`<BR>`bios_version`<BR>`cid`<BR>`city`<BR>`classification`<BR>`confidence`<BR>`country`<BR>`cpu_manufacturer`<BR>`creation_timestamp`<BR>`current_local_ip`<BR>`data_providers`<BR>`data_providers_count`<BR>`department`<BR>`descriptions`<BR>`discoverer_aids`<BR>`discoverer_count`<BR>`discoverer_platform_names`<BR>`discoverer_product_type_descs`<BR>`discoverer_tags`<BR>`email`<BR>`entity_type`<BR>`external_ip`<BR>`field_metadata`<BR>`first_discoverer_aid`<BR>`first_discoverer_ip`<BR>`first_seen_timestamp`<BR>`fqdn`<BR>`groups`<BR>`hostname`<BR>`id`<BR>`internet_exposure`<BR>`kernel_version`<BR>`last_discoverer_aid`<BR>`last_seen_timestamp`<BR>`local_ip_addresses`<BR>`local_ips_count`<BR>`location`<BR>`mac_addresses`<BR>`machine_domain`<BR>`managed_by`<BR>`network_interfaces`<BR>`network_interfaces.interface_alias`<BR>`network_interfaces.interface_description`<BR>`network_interfaces.local_ip`<BR>`network_interfaces.mac_address`<BR>`network_interfaces.network_prefix`<BR>`number_of_disk_drives`<BR>`object_guid`<BR>`object_sid`<BR>`os_is_eol`<BR>`os_service_pack`<BR>`os_version`<BR>`ou`<BR>`owned_by`<BR>`physical_core_count`<BR>`platform_name`<BR>`processor_package_count`<BR>`product_type`<BR>`product_type_desc`<BR>`reduced_functionality_mode`<BR>`servicenow_id`<BR>`site_name`<BR>`state`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`system_serial_number`<BR>`tags`<BR>`used_for`<BR><BR>Account:<BR>`account_name`<BR>`account_type`<BR>`admin_privileges`<BR>`cid`<BR>`first_seen_timestamp`<BR>`id`<BR>`last_failed_login_hostname`<BR>`last_failed_login_timestamp`<BR>`last_failed_login_type`<BR>`last_successful_login_host_city`<BR>`last_successful_login_host_country`<BR>`last_successful_login_hostname`<BR>`last_successful_login_remote_ip`<BR>`last_successful_login_timestamp`<BR>`last_successful_login_type`<BR>`login_domain`<BR>`password_last_set_timestamp`<BR>`user_sid`<BR>`username`<BR><BR>IoT:<BR>`device_family`<BR>`device_class`<BR>`device_type`<BR>`device_mode`<BR>`business_criticality`<BR>`line_of_business`<BR>`virtual_zone`<BR>`subnet`<BR>`purdue_level`<BR>`vlan`<BR>`local_ip_addresses`<BR>`mac_addresses`<BR>`physical_connections_count`<BR>`data_providers`<BR><BR>Login:<BR>`account_id`<BR>`account_name`<BR>`account_type`<BR>`admin_privileges`<BR>`aggregation_time_interval`<BR>`aid`<BR>`cid`<BR>`failure_description`<BR>`host_city`<BR>`host_country`<BR>`host_id`<BR>`hostname`<BR>`id`<BR>`is_suspicious`<BR>`local_ip`<BR>`login_domain`<BR>`login_event_count`<BR>`login_status`<BR>`login_timestamp`<BR>`login_type`<BR>`remote_ip`<BR>`user_sid`<BR>`username`||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`100`||||
|Include|String[]|Include additional properties|||`login_event`|||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
|Account|Switch|Search for user account assets||||||
|Application|Switch|Search for applications||||||
|IoT|Switch|Search for IoT assets||||||
|Login|Switch|Search for login events||||||
## SYNTAX
```powershell
Get-FalconAsset [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset -Id <String[]> -Login [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset -Id <String[]> -IoT [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset -Id <String[]> -Application [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset -Id <String[]> -Account [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] -Login [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] -IoT [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] -Application [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAsset [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-Detailed] [-All] [-Total] -Account [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /discover/entities/accounts/v1
GET /discover/entities/applications/v1
GET /discover/entities/hosts/v1
GET /discover/entities/iot-hosts/v1
GET /discover/entities/logins/v1
GET /discover/queries/accounts/v1
GET /discover/queries/applications/v1
GET /discover/queries/hosts/v1
GET /discover/queries/iot-hosts/v1
GET /discover/queries/logins/v1
```
### falconpy
[query_hosts](https://github.com/CrowdStrike/falconpy/wiki/discover#query_hosts)<BR>[get_logins](https://github.com/CrowdStrike/falconpy/wiki/discover#get_logins)<BR>[get_iot_hosts](https://github.com/CrowdStrike/falconpy/wiki/discover#get_iot_hosts)<BR>[get_hosts](https://github.com/CrowdStrike/falconpy/wiki/discover#get_hosts)<BR>[get_applications](https://github.com/CrowdStrike/falconpy/wiki/discover#get_applications)<BR>[get_accounts](https://github.com/CrowdStrike/falconpy/wiki/discover#get_accounts)<BR>[query_logins](https://github.com/CrowdStrike/falconpy/wiki/discover#query_logins)<BR>[query_iot_hosts](https://github.com/CrowdStrike/falconpy/wiki/discover#query_iot_hosts)<BR>[query_applications](https://github.com/CrowdStrike/falconpy/wiki/discover#query_applications)<BR>[query_accounts](https://github.com/CrowdStrike/falconpy/wiki/discover#query_accounts)
## USAGE
### Find Unmanaged Assets within a given Subnet
```powershell
Get-FalconAsset -Filter "entity_type:'unmanaged'+network_interfaces.local_ip:'192.168.25.0/24'" [-Detailed] [-All]
```
### Find assets using a filtered search
```powershell
Get-FalconAsset -Filter "entity_type:'managed'+product_type_desc:'Workstation'+platform_name:'Windows'+last_seen_timestamp:>'now-7d'" [-Detailed] [-All]
```
### Get information about specific assets
```powershell
Get-FalconAsset -Id <id>, <id>
```

_2024-02-08: PSFalcon v2.2.6_
