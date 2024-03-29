# Update-FalconSession
## SYNOPSIS
Refresh a single-host or batch Real-time Response session to prevent expiration
## DESCRIPTION
Real-time Response sessions expire after 5 minutes by default. Any commands that were issued to a session that
take longer than 5 minutes will not return results without refreshing the session to keep it alive until the
command process completes.

Requires 'Real time response: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|QueueOffline|Boolean|Add non-responsive hosts to the offline queue||||||
|HostToRemove|String[]|Host identifier(s) to remove from a batch Real-time Response session||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 30]|`1`|`600`||||
|HostId|String|Host identifier, for a single-host session||||X|X|
|BatchId|String|Batch session identifier|||||X|
## SYNTAX
```powershell
Update-FalconSession [[-QueueOffline] <Boolean>] -HostId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Update-FalconSession [[-QueueOffline] <Boolean>] [[-HostToRemove] <String[]>] [[-Timeout] <Int32>] -BatchId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/combined/batch-refresh-session/v1
POST /real-time-response/entities/refresh-session/v1
```
### falconpy
[RTR_PulseSession](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_PulseSession)<BR>[BatchRefreshSessions](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#BatchRefreshSessions)
## USAGE
### Refresh a batch session to prevent expiration
**NOTE**: Required when you expect to exceed the default session expiration time \(5 minutes\).
```powershell
Update-FalconSession -BatchId $Batch.batch_id
```
### Refresh a single-host session to prevent expiration
**NOTE**: Required when you expect to exceed the default session expiration time \(5 minutes\).
```powershell
Update-FalconSession -SessionId $Session.session_id
```

_See [Start-FalconSession](Start-FalconSession)_.

_2023-04-25: PSFalcon v2.2.5_
