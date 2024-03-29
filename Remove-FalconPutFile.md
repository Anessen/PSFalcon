# Remove-FalconPutFile
## SYNOPSIS
Remove a Real-time Response 'put' file
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Real-time Response 'put' file identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconPutFile [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /real-time-response/entities/put-files/v1
```
### falconpy
[RTR_DeletePut_Files](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_DeletePut_Files)
## USAGE
### Delete 'put' files
```powershell
Remove-FalconPutFile -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
