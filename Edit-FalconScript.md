# Edit-FalconScript
## SYNOPSIS
Modify a Real-time Response script
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Platform|String[]|Operating system platform|||`windows`<BR>`mac`<BR>`linux`||X|
|PermissionType|String|Permission level [public: 'Administrators' and 'Active Responders', group: 'Administrators', private: creator]|||`private`<BR>`group`<BR>`public`||X|
|Name|String|Script name|||||X|
|Description|String|Script description|||||X|
|Comment|String|Audit log comment|`1`|`4096`|||X|
|Path|String|Path to script file|||||X|
|Id|String|Script identifier|||||X|
## SYNTAX
```powershell
Edit-FalconScript [[-Platform] <String[]>] [[-PermissionType] <String>] [[-Name] <String>] [[-Description] <String>] [[-Comment] <String>] [-Path] <String> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /real-time-response/entities/scripts/v1
```
### falconpy
[RTR_UpdateScripts](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_UpdateScripts)
## USAGE
### Modify scripts
```powershell
Edit-FalconScript -Id <id> -Name new_script_name
```
```powershell
Get-FalconScript -Filter "name:'my_script'" | Edit-FalconScript -Id <id> -Name new_script_name
```

_2023-04-25: PSFalcon v2.2.5_
