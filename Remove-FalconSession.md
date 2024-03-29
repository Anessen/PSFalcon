# Remove-FalconSession
## SYNOPSIS
Remove a Real-time Response session
## DESCRIPTION
Requires 'Real time response: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Session identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconSession [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /real-time-response/entities/sessions/v1
```
### falconpy
[RTR_DeleteSession](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_DeleteSession)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
