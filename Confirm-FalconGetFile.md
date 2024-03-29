# Confirm-FalconGetFile
## SYNOPSIS
Verify the status of a Real-time Response 'get' command
## DESCRIPTION
Requires 'Real time response: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SessionId|String|Session identifier|||||X|
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 30]|`1`|`600`||||
|BatchGetCmdReqId|String|Batch 'get' command identifier|||||X|
## SYNTAX
```powershell
Confirm-FalconGetFile [[-Timeout] <Int32>] -BatchGetCmdReqId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Confirm-FalconGetFile -SessionId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /real-time-response/combined/batch-get-command/v1
GET /real-time-response/entities/file/v2
```
### falconpy
[BatchGetCmdStatus](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#BatchGetCmdStatus)<BR>[RTR_ListFilesV2](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListFilesV2)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
