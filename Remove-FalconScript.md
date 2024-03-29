# Remove-FalconScript
## SYNOPSIS
Remove a custom Real-time Response script
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Script identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconScript [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /real-time-response/entities/scripts/v1
```
### falconpy
[RTR_DeleteScripts](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_DeleteScripts)
## USAGE
### Delete scripts
```powershell
Remove-FalconScript -Id <id>, <id>
```
### Delete scripts matching a filter
```powershell
Get-FalconScript -Filter "name:'my_script'" | Remove-FalconScript
```

_2023-04-25: PSFalcon v2.2.5_
