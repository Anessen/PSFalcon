# Edit-FalconInstallToken
## SYNOPSIS
Modify installation tokens
## DESCRIPTION
Requires 'Installation tokens: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Label|String|Installation token label|||||X|
|ExpiresTimestamp|String|Installation token expiration time (RFC3339), or 'null'|||||X|
|Revoked|Boolean|Set revocation status|||||X|
|Id|String[]|Installation token identifier|||||X|
## SYNTAX
```powershell
Edit-FalconInstallToken [[-Label] <String>] [[-ExpiresTimestamp] <String>] [[-Revoked] <Boolean>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /installation-tokens/entities/tokens/v1
```
### falconpy
[tokens_update](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#tokens_update)
## USAGE
### Revoke a token
```powershell
Edit-FalconInstallToken -Id <id> -Revoked $true
```
### Rename a token and set it to never expire
```powershell
Edit-FalconInstallToken -Id <id> -Label "Token no expiration" -ExpiresTimestamp null
```

_2023-04-25: PSFalcon v2.2.5_
