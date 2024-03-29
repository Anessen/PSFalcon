# Confirm-FalconAdminCommand
## SYNOPSIS
Verify the status of a Real-time Response 'admin' command issued to a single-host session
## DESCRIPTION
Confirms the status of an executed 'admin' command. The single-host Real-time Response APIs require that commands
be confirmed to 'acknowledge' that they have been processed as part of your API-based workflow. Failing to confirm
after commands can lead to unexpected results.

A 'sequence_id' value of 0 is added if the parameter is not specified.

Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SequenceId|Int32|Sequence identifier||||||
|CloudRequestId|String|Command request identifier||||X|X|
## SYNTAX
```powershell
Confirm-FalconAdminCommand [[-SequenceId] <Int32>] [-CloudRequestId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /real-time-response/entities/admin-command/v1
```
### falconpy
[RTR_CheckAdminCommandStatus](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_CheckAdminCommandStatus)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
