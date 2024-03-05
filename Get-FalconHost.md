# Get-FalconHost
## SYNOPSIS
Search for hosts
## DESCRIPTION
Requires 'Hosts: Read' plus related permission(s) for 'Include' selection(s).
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Host identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`agent_load_flags`<BR>`agent_version`<BR>`bios_manufacturer`<BR>`bios_version`<BR>`cid`<BR>`config_id_base`<BR>`config_id_build`<BR>`config_id_platform`<BR>`cpu_signature`<BR>`device_id`<BR>`external_ip`<BR>`first_seen`<BR>`groups`<BR>`hostname`<BR>`instance_id`<BR>`kernel_version`<BR>`last_login_timestamp`<BR>`last_seen`<BR>`local_ip`<BR>`local_ip.raw`<BR>`mac_address`<BR>`machine_domain`<BR>`major_version`<BR>`minor_version`<BR>`modified_timestamp`<BR>`os_version`<BR>`ou`<BR>`platform_id`<BR>`platform_name`<BR>`product_type_desc`<BR>`reduced_functionality_mode`<BR>`release_group`<BR>`serial_number`<BR>`site_name`<BR>`status`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`||||||
|Sort|String|Property and direction to sort results|||`device_id.asc`<BR>`device_id.desc`<BR>`agent_load_flags.asc`<BR>`agent_load_flags.desc`<BR>`agent_version.asc`<BR>`agent_version.desc`<BR>`bios_manufacturer.asc`<BR>`bios_manufacturer.desc`<BR>`bios_version.asc`<BR>`bios_version.desc`<BR>`config_id_base.asc`<BR>`config_id_base.desc`<BR>`config_id_build.asc`<BR>`config_id_build.desc`<BR>`config_id_platform.asc`<BR>`config_id_platform.desc`<BR>`cpu_signature.asc`<BR>`cpu_signature.desc`<BR>`external_ip.asc`<BR>`external_ip.desc`<BR>`first_seen.asc`<BR>`first_seen.desc`<BR>`hostname.asc`<BR>`hostname.desc`<BR>`instance_id.asc`<BR>`instance_id.desc`<BR>`last_login_timestamp.asc`<BR>`last_login_timestamp.desc`<BR>`last_seen.asc`<BR>`last_seen.desc`<BR>`local_ip.asc`<BR>`local_ip.desc`<BR>`local_ip.raw.asc`<BR>`local_ip.raw.desc`<BR>`mac_address.asc`<BR>`mac_address.desc`<BR>`machine_domain.asc`<BR>`machine_domain.desc`<BR>`major_version.asc`<BR>`major_version.desc`<BR>`minor_version.asc`<BR>`minor_version.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`os_version.asc`<BR>`os_version.desc`<BR>`ou.asc`<BR>`ou.desc`<BR>`platform_id.asc`<BR>`platform_id.desc`<BR>`platform_name.asc`<BR>`platform_name.desc`<BR>`product_type_desc.asc`<BR>`product_type_desc.desc`<BR>`reduced_functionality_mode.asc`<BR>`reduced_functionality_mode.desc`<BR>`release_group.asc`<BR>`release_group.desc`<BR>`serial_number.asc`<BR>`serial_number.desc`<BR>`site_name.asc`<BR>`site_name.desc`<BR>`status.asc`<BR>`status.desc`<BR>`system_manufacturer.asc`<BR>`system_manufacturer.desc`<BR>`system_product_name.asc`<BR>`system_product_name.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Include|String[]|Include additional properties|||`group_names`<BR>`login_history`<BR>`network_history`<BR>`online_state`<BR>`policy_names`<BR>`zero_trust_assessment`|||
|Offset|String|Position to begin retrieving results||||||
|Hidden|Switch|Restrict search to 'hidden' hosts||||||
|Login|Switch|Retrieve user login history||||||
|Network|Switch|Retrieve network address history||||||
|State|Switch|Retrieve online status||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHost -Id <String[]> -State [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHost -Id <String[]> -Network [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHost -Id <String[]> -Login [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHost -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconHost [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <String>] -Hidden [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /devices/entities/online-state/v1
GET /devices/queries/devices-hidden/v1
GET /devices/queries/devices-scroll/v1
POST /devices/combined/devices/login-history/v2
POST /devices/combined/devices/network-address-history/v1
POST /devices/entities/devices/v2
```
### falconpy
[QueryDevicesByFilterScroll](https://github.com/CrowdStrike/falconpy/wiki/hosts#QueryDevicesByFilterScroll)<BR>[GetOnlineState_V1](https://github.com/CrowdStrike/falconpy/wiki/hosts#GetOnlineState_V1)<BR>[QueryGetNetworkAddressHistoryV1](https://github.com/CrowdStrike/falconpy/wiki/hosts#QueryGetNetworkAddressHistoryV1)<BR>[QueryDeviceLoginHistoryV2](https://github.com/CrowdStrike/falconpy/wiki/hosts#QueryDeviceLoginHistoryV2)<BR>[PostDeviceDetailsV2](https://github.com/CrowdStrike/falconpy/wiki/hosts#PostDeviceDetailsV2)<BR>[QueryHiddenDevices](https://github.com/CrowdStrike/falconpy/wiki/hosts#QueryHiddenDevices)
## USAGE
**NOTE**: The `Include` parameter can be used to append additional output to a `Get-FalconHost` result.
### Finding all Windows hosts
```powershell
Get-FalconHost -Filter "platform_name:'Windows'" [-Detailed] [-All]
```
### Finding all hosts in last # of days
```powershell
Get-FalconHost -Filter "last_seen:>'last 3 days'" [-Detailed] [-All]
```
### Finding Falcon hosts that match a given AWS instance ID
```powershell
Get-FalconHost -Filter "instance_id:'<instance_id>'" [-Detailed] [-All]
```
### Finding hosts based on multiple query criteria
```powershell
Get-FalconHost -Filter "product_type_desc:'Workstation'+status:'normal'+platform_name:['Windows','Mac']+last_seen:>='2020-07-04'" [-Detailed] [-All]
```
_See [Find-FalconHostname](Find-FalconHostname)._
### Retrieving a list of the first 100 hosts in your environment
```powershell
Get-FalconHost [-Detailed]
```
### Getting host details
```powershell
Get-FalconHost -Id <id>, <id>
```
### Retrieving host NIC history
```powershell
Get-FalconHost -Id <id>, <id> -Network
```
### Retrieving info about last logged in users
```powershell
Get-FalconHost -Id <id>, <id> -Login
```
### Finding hosts that have been deleted
```powershell
Get-FalconHost -Hidden [-Detailed] [-All]
```

_2024-03-05: PSFalcon v2.2.6_
