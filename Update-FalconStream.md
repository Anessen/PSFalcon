# Update-FalconStream
## SYNOPSIS
Refresh an active event stream
## DESCRIPTION
Requires 'Event streams: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|AppId|String|Connection label||||||
|Partition|Int32|Partition number||||||
## SYNTAX
```powershell
Update-FalconStream [-AppId] <String> [-Partition] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /sensors/entities/datafeed-actions/v1/{partition}
```
### falconpy
[refreshActiveStreamSession](https://github.com/CrowdStrike/falconpy/wiki/event-streams#refreshActiveStreamSession)
## USAGE
### Refresh an active event stream
```powershell
Update-FalconStream -AppId psfalcon -Partition 0
```

_2023-04-25: PSFalcon v2.2.5_
