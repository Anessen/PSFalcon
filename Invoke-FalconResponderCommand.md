# Invoke-FalconResponderCommand
## SYNOPSIS
Issue a Real-time Response active-responder command to an existing single-host or batch session
## DESCRIPTION
Sessions can be started using 'Start-FalconSession'. A successfully created session will contain a 'session_id'
or 'batch_id' value which can be used with the '-SessionId' or '-BatchId' parameters.

The 'Wait' parameter will use 'Confirm-FalconResponderCommand' or 'Confirm-FalconGetFile' to check for command
results every 20 seconds until complete or processing ends.

Requires 'Real time response: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Command|String|Real-time Response command|||`cat`<BR>`cd`<BR>`clear`<BR>`cp`<BR>`csrutil`<BR>`encrypt`<BR>`env`<BR>`eventlog backup`<BR>`eventlog export`<BR>`eventlog list`<BR>`eventlog view`<BR>`filehash`<BR>`get`<BR>`getsid`<BR>`help`<BR>`history`<BR>`ifconfig`<BR>`ipconfig`<BR>`kill`<BR>`ls`<BR>`map`<BR>`memdump`<BR>`mkdir`<BR>`mount`<BR>`mv`<BR>`netstat`<BR>`ps`<BR>`reg delete`<BR>`reg load`<BR>`reg query`<BR>`reg set`<BR>`reg unload`<BR>`restart`<BR>`rm`<BR>`runscript`<BR>`shutdown`<BR>`umount`<BR>`unmap`<BR>`update history`<BR>`update install`<BR>`update list`<BR>`update install`<BR>`users`<BR>`xmemdump`<BR>`zip`|||
|Argument|String|Arguments to include with the command||||||
|OptionalHostId|String[]|Restrict execution to specific host identifiers||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 30]|`1`|`600`||||
|HostTimeout|Int32|Length of time to wait for a result from target host(s), in seconds|`1`|`600`||||
|SessionId|String|Session identifier|||||X|
|BatchId|String|Batch session identifier|||||X|
|Wait|Switch|Use 'Confirm-FalconResponderCommand' or 'Confirm-FalconGetFile' to retrieve command result||||||
## SYNTAX
```powershell
Invoke-FalconResponderCommand [-Command] <String> [[-Argument] <String>] [[-OptionalHostId] <String[]>] [[-Timeout] <Int32>] [[-HostTimeout] <Int32>] -BatchId <String> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconResponderCommand [-Command] <String> [[-Argument] <String>] -SessionId <String> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/combined/batch-active-responder-command/v1
POST /real-time-response/entities/active-responder-command/v1
```
### falconpy
[BatchActiveResponderCmd](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#BatchActiveResponderCmd)<BR>[RTR_ExecuteActiveResponderCommand](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ExecuteActiveResponderCommand)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
