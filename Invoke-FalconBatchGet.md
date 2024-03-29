# Invoke-FalconBatchGet
## SYNOPSIS
Issue a Real-time Response batch 'get' command to an existing batch session
## DESCRIPTION
When a 'get' command has been issued, the 'batch_get_cmd_req_id' property will be returned. That value is used
to verify the completion of the file transfer using 'Confirm-FalconGetFile'.

The 'Wait' parameter will use 'Confirm-FalconGetFile' to check for command results every 20 seconds until complete
or processing ends.

Requires 'Real time response: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|FilePath|String|Path to file on target host||||||
|OptionalHostId|String[]|Restrict execution to specific host identifiers||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 30]|`1`|`600`||||
|HostTimeout|Int32|Length of time to wait for a result from target host(s), in seconds|`1`|`600`||||
|BatchId|String|Batch session identifier||||X|X|
|Wait|Switch|Use 'Confirm-FalconGetFile' to retrieve command result||||||
## SYNTAX
```powershell
Invoke-FalconBatchGet [-FilePath] <String> [[-OptionalHostId] <String[]>] [[-Timeout] <Int32>] [[-HostTimeout] <Int32>] -BatchId <String> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/combined/batch-get-command/v1
```
### falconpy
[BatchGetCmd](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#BatchGetCmd)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
