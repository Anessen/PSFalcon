# Remove-FalconGroupingTag
## SYNOPSIS
Remove FalconGroupingTags from hosts
## DESCRIPTION
Requires 'Hosts: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Tag|String[]|FalconGroupingTag value ['FalconGroupingTags/<string>']||||||
|Id|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconGroupingTag [-Tag] <String[]> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /devices/entities/devices/tags/v1
```
### falconpy
[UpdateDeviceTags](https://github.com/CrowdStrike/falconpy/wiki/hosts#UpdateDeviceTags)
## USAGE
### Removing Falcon grouping tags
```powershell
Remove-FalconGroupingTag -Id <id>, <id> -Tags FalconGroupingTags/tag1, FalconGroupingTags/tag2
```

_2023-04-25: PSFalcon v2.2.5_
