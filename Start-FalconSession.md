# Start-FalconSession
## SYNOPSIS
Initialize a single-host or batch Real-time Response session
## DESCRIPTION
Real-time Response sessions require Host identifier values. Sessions that are successfully started return a
'session_id' (for single hosts) or 'batch_id' (multiple hosts) value which can be used to issue commands that
will be processed by the host(s) in the session.

Commands can be issued using 'Invoke-FalconCommand', 'Invoke-FalconResponderCommand', 'Invoke-FalconAdminCommand'
and 'Invoke-FalconBatchGet'.

Requires 'Real time response: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|QueueOffline|Boolean|Add non-responsive hosts to the offline queue||||||
|ExistingBatchId|String|Add hosts to an existing batch session||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 30]|`1`|`600`||||
|HostTimeout|Int32|Length of time to wait for a result from target host(s), in seconds|`1`|`600`||||
|Id|String[]|Host identifier|`1`|`10000`||X|X|
## SYNTAX
```powershell
Start-FalconSession [[-QueueOffline] <Boolean>] [[-ExistingBatchId] <String>] [[-Timeout] <Int32>] [[-HostTimeout] <Int32>] -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Start-FalconSession [[-QueueOffline] <Boolean>] [[-Timeout] <Int32>] -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/combined/batch-init-session/v1
POST /real-time-response/entities/sessions/v1
```
### falconpy
[BatchInitSessions](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#BatchInitSessions)<BR>[RTR_InitSession](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_InitSession)
## USAGE
### Start a batch session with multiple hosts
```powershell
$Batch = Start-FalconSession -Id <id>, <id>
```
### Start a session with a single host
```powershell
$Session = Start-FalconSession -Id <id>
```

_See [Invoke-FalconCommand](Invoke-FalconCommand)_.

_See [Invoke-FalconResponderCommand](Invoke-FalconResponderCommand)_.

_See [Invoke-FalconAdminCommand](Invoke-FalconAdminCommand)_.

_See [Invoke-FalconBatchGet](Invoke-FalconBatchGet)_.

_See [Update-FalconSession](Update-FalconSession)_.

_2023-04-25: PSFalcon v2.2.5_
