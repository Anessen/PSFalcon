# Revoke-FalconToken
## SYNOPSIS
Revoke your active OAuth2 access token
## DESCRIPTION
Revokes your active OAuth2 access token and clears cached credential information ('ClientId', 'ClientSecret',
'MemberCid', 'Cloud'/'Hostname') from the module.
## SYNTAX
```powershell
Revoke-FalconToken [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /oauth2/revoke
```
### falconpy
[oauth2RevokeToken](https://github.com/CrowdStrike/falconpy/wiki/oauth2#oauth2RevokeToken)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
