# Get-FalconQueue
## SYNOPSIS
Create a report of Real-time Response commands in the offline queue
## DESCRIPTION
Creates a CSV of pending Real-time Response commands and their related session information. By default, sessions
within the offline queue expire 7 days after creation. Sessions can have additional commands appended to them to
extend their expiration time.

Additional host information can be appended to the results using the 'Include' parameter.

Requires 'Real time response: Read', 'Real time response: Write' and 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Days|Int32|Number of days worth of sessions to retrieve [default: 7]||||||
|Include|String[]|Include additional properties|||`agent_version`<BR>`cid`<BR>`external_ip`<BR>`first_seen`<BR>`host_hidden_status`<BR>`hostname`<BR>`last_seen`<BR>`local_ip`<BR>`mac_address`<BR>`os_build`<BR>`os_version`<BR>`platform_name`<BR>`product_type`<BR>`product_type_desc`<BR>`reduced_functionality_mode`<BR>`serial_number`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`|||
|HostId|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Get-FalconQueue [[-Days] <Int32>] [[-Include] <String[]>] [[-HostId] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/entities/queued-sessions/GET/v1
```
### falconpy
[RTR_ListQueuedSessions](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListQueuedSessions)
## USAGE
`Get-FalconQueue` will create a CSV file with information about sessions that have pending queued commands or have been created in the last 7 days (by default).
```powershell
Get-FalconQueue [-Days]
```

_2023-05-09: PSFalcon v2.2.5_
