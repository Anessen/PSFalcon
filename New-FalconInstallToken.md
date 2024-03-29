# New-FalconInstallToken
## SYNOPSIS
Create an installation token
## DESCRIPTION
Requires 'Installation tokens: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Label|String|Installation token label||||||
|ExpiresTimestamp|String|Installation token expiration time (RFC3339), or 'null'||||||
## SYNTAX
```powershell
New-FalconInstallToken [-Label] <String> [-ExpiresTimestamp] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /installation-tokens/entities/tokens/v1
```
### falconpy
[tokens_create](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#tokens_create)
## USAGE
### Create an installation token
```powershell
New-FalconInstallToken -Label "My Token" -ExpiresTimestamp "2021-12-31T00:00:00Z"
```

_2023-04-25: PSFalcon v2.2.5_
