# Request-FalconToken
## SYNOPSIS
Request an OAuth2 access token
## DESCRIPTION
If successful, your credentials ('ClientId', 'ClientSecret', 'MemberCid' and 'Cloud'/'CustomUrl'/'Hostname') and
token are cached for re-use.

If an active OAuth2 access token is due to expire in less than 60 seconds, a new token will automatically be
requested using your cached credentials.

The 'Collector' parameter allows for the submission of a [System.Collections.Hashtable] object containing the
parameters included with a 'Register-FalconEventCollector' command ('Path', 'Token' and 'Enabled') in order to
log an initial OAuth2 access token request.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|ClientId|String|OAuth2 client identifier|||||X|
|ClientSecret|String|OAuth2 client secret|||||X|
|Cloud|String|CrowdStrike cloud [default: 'us-1']|||`eu-1`<BR>`us-gov-1`<BR>`us-1`<BR>`us-2`||X|
|CustomUrl|String|Custom API URL for module troubleshooting|||||X|
|Hostname|String|CrowdStrike API hostname|||`https://api.crowdstrike.com`<BR>`https://api.us-2.crowdstrike.com`<BR>`https://api.laggar.gcw.crowdstrike.com`<BR>`https://api.eu-1.crowdstrike.com`||X|
|MemberCid|String|Member CID, used when authenticating within a multi-CID environment ('Falcon Flight Control')|||||X|
|Collector|Hashtable|A hashtable containing 'Path', 'Token' and 'Enabled' properties for 'Register-FalconEventCollector'|||||X|
## SYNTAX
```powershell
Request-FalconToken [[-ClientId] <String>] [[-ClientSecret] <String>] [[-Hostname] <String>] [[-MemberCid] <String>] [[-Collector] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Request-FalconToken [[-ClientId] <String>] [[-ClientSecret] <String>] [[-CustomUrl] <String>] [[-MemberCid] <String>] [[-Collector] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Request-FalconToken [[-ClientId] <String>] [[-ClientSecret] <String>] [[-Cloud] <String>] [[-MemberCid] <String>] [[-Collector] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /oauth2/token
```
### falconpy
[oauth2AccessToken](https://github.com/CrowdStrike/falconpy/wiki/oauth2#oauth2AccessToken)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
