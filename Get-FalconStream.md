# Get-FalconStream
## SYNOPSIS
Retrieve event streams
## DESCRIPTION
Requires 'Event streams: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|AppId|String|Connection label||||||
|Format|String|Format for streaming events [default: json]|||`json`<BR>`flatjson`|||
## SYNTAX
```powershell
Get-FalconStream [-AppId] <String> [[-Format] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /sensors/entities/datafeed/v2
```
### falconpy
[listAvailableStreamsOAuth2](https://github.com/CrowdStrike/falconpy/wiki/event-streams#listAvailableStreamsOAuth2)
## USAGE
### Start an event stream
```powershell
Get-FalconStream -AppId psfalcon
```

_2023-04-25: PSFalcon v2.2.5_
