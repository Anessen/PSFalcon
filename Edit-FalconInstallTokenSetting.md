# Edit-FalconInstallTokenSetting
## SYNOPSIS
Update installation token settings
## DESCRIPTION
Requires 'Installation token settings: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|TokenRequired|Boolean|||||||
|MaxActiveToken|Int32|Maximum number of active installation tokens||||||
## SYNTAX
```powershell
Edit-FalconInstallTokenSetting [[-TokenRequired] <Boolean>] [[-MaxActiveToken] <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /installation-tokens/entities/customer-settings/v1
```
### falconpy
[customer_settings_update](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#customer_settings_update)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
