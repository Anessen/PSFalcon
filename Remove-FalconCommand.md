# Remove-FalconCommand
## SYNOPSIS
Remove a command from a queued Real-time Response session
## DESCRIPTION
Requires 'Real time response: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SessionId|String|Session identifier|||||X|
|CloudRequestId|String|Cloud request identifier|||||X|
## SYNTAX
```powershell
Remove-FalconCommand [-SessionId] <String> [-CloudRequestId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /real-time-response/entities/queued-sessions/command/v1
```
### falconpy
[RTR_DeleteQueuedSession](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_DeleteQueuedSession)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
