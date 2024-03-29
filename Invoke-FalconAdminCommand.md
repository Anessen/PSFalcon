# Invoke-FalconAdminCommand
## SYNOPSIS
Issue a Real-time Response admin command to an existing single-host or batch session
## DESCRIPTION
Sessions can be started using 'Start-FalconSession'. A successfully created session will contain a 'session_id'
or 'batch_id' value which can be used with the '-SessionId' or '-BatchId' parameters.

The 'Wait' parameter will use 'Confirm-FalconAdminCommand' or 'Confirm-FalconGetFile' to check for command
results every 20 seconds until complete or processing ends.

Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Command|String|Real-time Response command|||`cat`<BR>`cd`<BR>`clear`<BR>`cp`<BR>`csrutil`<BR>`cswindiag`<BR>`encrypt`<BR>`env`<BR>`eventlog backup`<BR>`eventlog export`<BR>`eventlog list`<BR>`eventlog view`<BR>`falconscript`<BR>`filehash`<BR>`get`<BR>`getsid`<BR>`help`<BR>`history`<BR>`ifconfig`<BR>`ipconfig`<BR>`kill`<BR>`ls`<BR>`map`<BR>`memdump`<BR>`mkdir`<BR>`mount`<BR>`mv`<BR>`netstat`<BR>`ps`<BR>`put`<BR>`put-and-run`<BR>`reg delete`<BR>`reg load`<BR>`reg query`<BR>`reg set`<BR>`reg unload`<BR>`restart`<BR>`rm`<BR>`run`<BR>`runscript`<BR>`shutdown`<BR>`umount`<BR>`unmap`<BR>`update history`<BR>`update install`<BR>`update list`<BR>`update install`<BR>`users`<BR>`xmemdump`<BR>`zip`|||
|Argument|String|Arguments to include with the command||||||
|OptionalHostId|String[]|Restrict execution to specific host identifiers||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 30]|`1`|`600`||||
|HostTimeout|Int32|Length of time to wait for a result from target host(s), in seconds|`1`|`600`||||
|SessionId|String|Session identifier|||||X|
|BatchId|String|Batch session identifier|||||X|
|Wait|Switch|Use 'Confirm-FalconAdminCommand' or 'Confirm-FalconGetFile' to retrieve command result||||||
## SYNTAX
```powershell
Invoke-FalconAdminCommand [-Command] <String> [[-Argument] <String>] [[-OptionalHostId] <String[]>] [[-Timeout] <Int32>] [[-HostTimeout] <Int32>] -BatchId <String> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconAdminCommand [-Command] <String> [[-Argument] <String>] -SessionId <String> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/combined/batch-admin-command/v1
POST /real-time-response/entities/admin-command/v1
```
### falconpy
[BatchAdminCmd](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#BatchAdminCmd)<BR>[RTR_ExecuteAdminCommand](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ExecuteAdminCommand)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
