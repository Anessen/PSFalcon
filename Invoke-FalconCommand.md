# Invoke-FalconCommand
## SYNOPSIS
Issue a Real-time Response read-only command to an existing single-host or batch session
## DESCRIPTION
Sessions can be started using 'Start-FalconSession'. A successfully created session will contain a 'session_id'
or 'batch_id' value which can be used with the '-SessionId' or '-BatchId' parameters.

The 'Wait' parameter will use 'Confirm-FalconCommand' to check for command results every 20 seconds until complete
or processing ends.

Requires 'Real time response: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Command|String|Real-time Response command|||`cat`<BR>`cd`<BR>`clear`<BR>`csrutil`<BR>`env`<BR>`eventlog backup`<BR>`eventlog export`<BR>`eventlog list`<BR>`eventlog view`<BR>`filehash`<BR>`getsid`<BR>`help`<BR>`history`<BR>`ifconfig`<BR>`ipconfig`<BR>`ls`<BR>`mount`<BR>`netstat`<BR>`ps`<BR>`reg query`<BR>`users`|||
|Argument|String|Arguments to include with the command||||||
|OptionalHostId|String[]|Restrict execution to specific host identifiers||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 30]|`1`|`600`||||
|HostTimeout|Int32|Length of time to wait for a result from target host(s), in seconds|`1`|`600`||||
|SessionId|String|Session identifier|||||X|
|BatchId|String|Batch session identifier|||||X|
|Wait|Switch|Use 'Confirm-FalconCommand' to retrieve command result||||||
## SYNTAX
```powershell
Invoke-FalconCommand [-Command] <String> [[-Argument] <String>] [[-OptionalHostId] <String[]>] [[-Timeout] <Int32>] [[-HostTimeout] <Int32>] -BatchId <String> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconCommand [-Command] <String> [[-Argument] <String>] -SessionId <String> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/combined/batch-command/v1
POST /real-time-response/entities/command/v1
```
### falconpy
[BatchCmd](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#BatchCmd)<BR>[RTR_ExecuteCommand](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ExecuteCommand)
## USAGE
### Send a command to a batch Real-time Response session using read-only permission
```powershell
Invoke-FalconCommand -Command ls -Argument C:\Windows -BatchId $Batch.batch_id
```
### Send a command to a single-host Real-time Response session using read-only permission
When using single-host sessions, commands must be confirmed to retrieve the results and notify the session that the command has completed.
```powershell
$Command = Invoke-FalconCommand -Command ls -Argument C:\Windows -SessionId $Session.session_id
```
_See [Start-FalconSession](Start-FalconSession)_.

_See [Confirm-FalconCommand](Confirm-FalconCommand)_.

_2023-04-25: PSFalcon v2.2.5_
