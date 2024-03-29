# Get-FalconInstallTokenSetting
## SYNOPSIS
Retrieve installation token settings
## DESCRIPTION
Returns the maximum number of allowed installation tokens, and whether or not they are required for
installation of the Falcon sensor.

Requires 'Installation tokens: Read'.
## SYNTAX
```powershell
Get-FalconInstallTokenSetting [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /installation-tokens/entities/customer-settings/v1
```
### falconpy
[customer_settings_read](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#customer_settings_read)
## USAGE
### View installation token settings
```powershell
Get-FalconInstallTokenSetting
```

_2023-04-25: PSFalcon v2.2.5_
