# Send-FalconScript
## SYNOPSIS
Upload a custom Real-time Response script
## DESCRIPTION
Requires 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Platform|String[]|Operating system platform|||`windows`<BR>`mac`<BR>`linux`||X|
|PermissionType|String|Permission level [public: 'Administrators' and 'Active Responders', group: 'Administrators', private: creator]|||`private`<BR>`group`<BR>`public`||X|
|Name|String|Script name|`1`|`32766`|||X|
|Description|String|Script description|||||X|
|Comment|String|Audit log comment|`1`|`4096`|||X|
|Path|String|Path to local file or string-based script content|||||X|
## SYNTAX
```powershell
Send-FalconScript [-Platform] <String[]> [-PermissionType] <String> [[-Name] <String>] [[-Description] <String>] [[-Comment] <String>] [-Path] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /real-time-response/entities/scripts/v1
```
### falconpy
[RTR_CreateScripts](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_CreateScripts)
## USAGE
### Create a new script
```powershell
Send-FalconScript -Path .\hello_world.ps1 -Platform windows -PermissionType group
```

_2023-11-27: PSFalcon v2.2.6_
