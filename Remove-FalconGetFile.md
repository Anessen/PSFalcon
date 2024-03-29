# Remove-FalconGetFile
## SYNOPSIS
Remove Real-time Response 'get' files
## DESCRIPTION
Delete files previously retrieved during a Real-time Response session. The required 'Id' and 'SessionId' values
are contained in the results of 'Start-FalconSession' and 'Invoke-FalconAdminCommand' or 'Invoke-FalconBatchGet'
commands.

Requires 'Real time response: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|SessionId|String|Session identifier|||||X|
|Id|String|Real-time Response 'get' file identifier|||||X|
## SYNTAX
```powershell
Remove-FalconGetFile [-SessionId] <String> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /real-time-response/entities/file/v2
```
### falconpy
[RTR_DeleteFileV2](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_DeleteFileV2)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
