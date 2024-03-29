# Uninstall-FalconSensor
## SYNOPSIS
Use Real-time Response to uninstall the Falcon sensor from a host
## DESCRIPTION
This command uses information from the registry and/or relevant Falcon command line utilities of the target host
to uninstall the Falcon sensor. If the sensor is damaged or malfunctioning, Real-time Response may not work
properly and/or the uninstallation may not succeed.

Requires 'Hosts: Read', 'Sensor update policies: Write', 'Real time response: Read', and 'Real Time Response
(Admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|QueueOffline|Boolean|Add command request to the offline queue||||||
|Include|String[]|Include additional properties|||`agent_version`<BR>`cid`<BR>`external_ip`<BR>`first_seen`<BR>`hostname`<BR>`last_seen`<BR>`local_ip`<BR>`mac_address`<BR>`os_build`<BR>`os_version`<BR>`platform_name`<BR>`product_type`<BR>`product_type_desc`<BR>`serial_number`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`|||
|Id|String|Host identifier||||X|X|
## SYNTAX
```powershell
Uninstall-FalconSensor [[-QueueOffline] <Boolean>] [[-Include] <String[]>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
