# Get-FalconHost
## PARAMETERS
|Name|Type|Minimum|Maximum|Values|Pattern|Pipeline|PipelineByName|Description|
|----|----|-------|-------|------|-------|--------|--------------|-----------|
|Id|String[]||||`^[a-fA-F0-9]{32}$`|`True`|`True`|Host identifier|
|Filter|String|||||`False`|`False`|Falcon Query Language expression to limit results|
|Sort|String|||`device_id.asc`,`device_id.desc`,`agent_load_flags.asc`,`agent_load_flags.desc`,`agent_version.asc`,`agent_version.desc`,`bios_manufacturer.asc`,`bios_manufacturer.desc`,`bios_version.asc`,`bios_version.desc`,`config_id_base.asc`,`config_id_base.desc`,`config_id_build.asc`,`config_id_build.desc`,`config_id_platform.asc`,`config_id_platform.desc`,`cpu_signature.asc`,`cpu_signature.desc`,`external_ip.asc`,`external_ip.desc`,`first_seen.asc`,`first_seen.desc`,`hostname.asc`,`hostname.desc`,`instance_id.asc`,`instance_id.desc`,`last_login_timestamp.asc`,`last_login_timestamp.desc`,`last_seen.asc`,`last_seen.desc`,`local_ip.asc`,`local_ip.desc`,`local_ip.raw.asc`,`local_ip.raw.desc`,`mac_address.asc`,`mac_address.desc`,`machine_domain.asc`,`machine_domain.desc`,`major_version.asc`,`major_version.desc`,`minor_version.asc`,`minor_version.desc`,`modified_timestamp.asc`,`modified_timestamp.desc`,`os_version.asc`,`os_version.desc`,`ou.asc`,`ou.desc`,`platform_id.asc`,`platform_id.desc`,`platform_name.asc`,`platform_name.desc`,`product_type_desc.asc`,`product_type_desc.desc`,`reduced_functionality_mode.asc`,`reduced_functionality_mode.desc`,`release_group.asc`,`release_group.desc`,`serial_number.asc`,`serial_number.desc`,`site_name.asc`,`site_name.desc`,`status.asc`,`status.desc`,`system_manufacturer.asc`,`system_manufacturer.desc`,`system_product_name.asc`,`system_product_name.desc`||`False`|`False`|Property and direction to sort results|
|Limit|Int32|`1`|`5000`|||`False`|`False`|Maximum number of results per request|
|Include|String[]|||`group_names`,`login_history`,`network_history`,`online_state`,`zero_trust_assessment`||`False`|`False`|Include additional properties|
|Offset|String|||||`False`|`False`|Position to begin retrieving results|
|Hidden|SwitchParameter|||||`False`|`False`|Restrict search to 'hidden' hosts|
|Login|SwitchParameter|||||`False`|`False`|Retrieve user login history|
|Network|SwitchParameter|||||`False`|`False`|Retrieve network address history|
|State|SwitchParameter|||||`False`|`False`|Retrieve online status|
|Detailed|SwitchParameter|||||`False`|`False`|Retrieve detailed information|
|All|SwitchParameter|||||`False`|`False`|Repeat requests until all available results are retrieved|
|Total|SwitchParameter|||||`False`|`False`|Display total result count instead of results|
## SYNTAX
```
Get-FalconHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <String>] [-Detailed] -All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```
Get-FalconHost -Id <String[]> -State [-WhatIf] [-Confirm] [<CommonParameters>]
```
```
Get-FalconHost -Id <String[]> -Network [-WhatIf] [-Confirm] [<CommonParameters>]
```
```
Get-FalconHost -Id <String[]> -Login [-WhatIf] [-Confirm] [<CommonParameters>]
```
```
Get-FalconHost -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```
Get-FalconHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <String>] -Hidden -Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
_Generated from v2.2.2 on 20220907_