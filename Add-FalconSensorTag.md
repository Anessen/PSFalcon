# Add-FalconSensorTag
## SYNOPSIS
Use Real-time Response to add FalconSensorTags to hosts
## DESCRIPTION
Provided FalconSensorTag values will be appended to any existing tags.

Requires 'Hosts: Read', 'Sensor update policies: Write' and 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Tag|String[]|FalconSensorTag value ['FalconSensorTags/<string>']||||||
|QueueOffline|Boolean|Add command request to the offline queue||||||
|Id|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Add-FalconSensorTag [-Tag] <String[]> [[-QueueOffline] <Boolean>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Adding Sensor grouping tags
`Add-FalconSensorTag` uses Real-time Response to add the tags to the target host(s).
```powershell
Add-FalconSensorTag -Id <id>, <id> -Tag tag1, tag2 [-QueueOffline]
```

_2023-04-25: PSFalcon v2.2.5_
