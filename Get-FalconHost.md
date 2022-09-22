# Get-FalconHost
﻿## SYNOPSIS
Search for hosts
## DESCRIPTION
Requires 'Hosts: Read' plus related permission(s) for 'Include' selection(s).
## PARAMETERS
|Name|Type|Min|Max|Pattern|Allowed|Pipeline|PipelineByName|Description|
|----|----|---|---|-------|-------|--------|--------------|-----------|
|Id|String[]|||`^[a-fA-F0-9]{32}$`||True|True|Host identifier|
|Filter|String|||||False|False|Falcon Query Language expression to limit results|
|Sort|String||||`device_id.asc`<BR>`device_id.desc`<BR>`agent_load_flags.asc`<BR>`agent_load_flags.desc`<BR>`agent_version.asc`<BR>`agent_version.desc`<BR>`bios_manufacturer.asc`<BR>`bios_manufacturer.desc`<BR>`bios_version.asc`<BR>`bios_version.desc`<BR>`config_id_base.asc`<BR>`config_id_base.desc`<BR>`config_id_build.asc`<BR>`config_id_build.desc`<BR>`config_id_platform.asc`<BR>`config_id_platform.desc`<BR>`cpu_signature.asc`<BR>`cpu_signature.desc`<BR>`external_ip.asc`<BR>`external_ip.desc`<BR>`first_seen.asc`<BR>`first_seen.desc`<BR>`hostname.asc`<BR>`hostname.desc`<BR>`instance_id.asc`<BR>`instance_id.desc`<BR>`last_login_timestamp.asc`<BR>`last_login_timestamp.desc`<BR>`last_seen.asc`<BR>`last_seen.desc`<BR>`local_ip.asc`<BR>`local_ip.desc`<BR>`local_ip.raw.asc`<BR>`local_ip.raw.desc`<BR>`mac_address.asc`<BR>`mac_address.desc`<BR>`machine_domain.asc`<BR>`machine_domain.desc`<BR>`major_version.asc`<BR>`major_version.desc`<BR>`minor_version.asc`<BR>`minor_version.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`os_version.asc`<BR>`os_version.desc`<BR>`ou.asc`<BR>`ou.desc`<BR>`platform_id.asc`<BR>`platform_id.desc`<BR>`platform_name.asc`<BR>`platform_name.desc`<BR>`product_type_desc.asc`<BR>`product_type_desc.desc`<BR>`reduced_functionality_mode.asc`<BR>`reduced_functionality_mode.desc`<BR>`release_group.asc`<BR>`release_group.desc`<BR>`serial_number.asc`<BR>`serial_number.desc`<BR>`site_name.asc`<BR>`site_name.desc`<BR>`status.asc`<BR>`status.desc`<BR>`system_manufacturer.asc`<BR>`system_manufacturer.desc`<BR>`system_product_name.asc`<BR>`system_product_name.desc`|False|False|Property and direction to sort results|
|Limit|Int32|`1`|`5000`|||False|False|Maximum number of results per request|
|Include|String[]||||`group_names`<BR>`login_history`<BR>`network_history`<BR>`online_state`<BR>`zero_trust_assessment`|False|False|Include additional properties|
|Offset|String|||||False|False|Position to begin retrieving results|
|Hidden|Switch|||||False|False|Restrict search to 'hidden' hosts|
|Login|Switch|||||False|False|Retrieve user login history|
|Network|Switch|||||False|False|Retrieve network address history|
|State|Switch|||||False|False|Retrieve online status|
|Detailed|Switch|||||False|False|Retrieve detailed information|
|All|Switch|||||False|False|Repeat requests until all available results are retrieved|
|Total|Switch|||||False|False|Display total result count instead of results|
## SYNTAX
```
Get-FalconHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <String>] [-Detailed] [-All] [-Total] [-WhatIf] -Confirm] [<CommonParameters>]
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
Get-FalconHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <String>] -Hidden [-Detailed] [-All] [-Total] -WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Finding all Windows hosts
```powershell
Get-FalconHost -Filter "platform_name:'Windows'" [-Detailed] [-All]
```
### Finding Falcon hosts that match a given AWS instance ID
```powershell
Get-FalconHost -Filter "instance_id:'<instance_id>'" [-Detailed] [-All]
```
### Finding hosts based on multiple query criteria
```powershell
Get-FalconHost -Filter "product_type_desc:'Workstation'+status:'normal'+platform_name:['Windows','Mac']+last_seen:>='2020-07-04'" [-Detailed] [-All]
```
### Retrieving a list of the first 100 hosts in your environment
```powershell
Get-FalconHost [-Detailed]
```
### Getting host details
```powershell
Get-FalconHost -Ids <id>, <id>
```
### Retrieving host NIC history
```powershell
Get-FalconHost -Ids <id>, <id> -Network
```
**NOTE**: The `-Include` parameter can be used to append NIC history to other `Get-FalconHost` output.
### Retrieving info about last logged in users
```powershell
Get-FalconHost -Ids <id>, <id> -Login
```
**NOTE**: The `-Include` parameter can be used to append login history to other `Get-FalconHost` output.

_Generated 20220922 using PSFalcon v2.2.3_
