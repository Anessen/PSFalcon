# Invoke-FalconHostAction
## SYNOPSIS
Perform actions on hosts
## DESCRIPTION
Requires 'Hosts: Write', plus related permission(s) for 'Include' selection(s).
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`contain`<BR>`lift_containment`<BR>`hide_host`<BR>`unhide_host`<BR>`detection_suppress`<BR>`detection_unsuppress`|||
|Include|String[]|Include additional properties|||`agent_version`<BR>`cid`<BR>`external_ip`<BR>`first_seen`<BR>`host_hidden_status`<BR>`hostname`<BR>`last_seen`<BR>`local_ip`<BR>`mac_address`<BR>`os_build`<BR>`os_version`<BR>`platform_name`<BR>`product_type`<BR>`product_type_desc`<BR>`reduced_functionality_mode`<BR>`serial_number`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`|||
|Id|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconHostAction [-Name] <String> [[-Include] <String[]>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /devices/entities/devices-actions/v2
```
### falconpy
[PerformActionV2](https://github.com/CrowdStrike/falconpy/wiki/hosts#PerformActionV2)
## USAGE
### Containing or lifting containment on hosts
```powershell
Invoke-FalconHostAction -Name contain -Id <id>, <id>
```
```powershell
Invoke-FalconHostAction -Name lift_containment -Id <id>, <id>
```
_See [Network contain a device by Hostname](https://github.com/CrowdStrike/psfalcon/blob/master/samples/hosts/network-contain-a-device-by-hostname.ps1)._

_See [Network contain a list of Hostnames from a CSV file](https://github.com/CrowdStrike/psfalcon/blob/master/samples/hosts/network-contain-a-list-of-hostnames-from-a-csv-file.ps1)._
### Deleting and restoring hosts
```powershell
Invoke-FalconHostAction -Name hide_host -Id <id>, <id>
```
```powershell
Invoke-FalconHostAction -Name unhide_host -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
