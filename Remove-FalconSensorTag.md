# Remove-FalconSensorTag
## SYNOPSIS
Use Real-time Response to remove FalconSensorTags from hosts
## DESCRIPTION
Provided FalconSensorTag values will be removed from existing tags and others will be left unmodified.

Requires 'Hosts: Read', 'Sensor update policies: Write' and 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Tag|String[]|FalconSensorTag value ['FalconSensorTags/<string>']||||||
|QueueOffline|Boolean|Add command request to the offline queue||||||
|Id|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconSensorTag [-Tag] <String[]> [[-QueueOffline] <Boolean>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Removing Sensor grouping tags
`Remove-FalconSensorTag` uses Real-time Response to remove the tags from the target host(s).
```powershell
Remove-FalconSensorTag -Id <id>, <id> -Tag tag1, tag2 [-QueueOffline]
```

_2023-04-25: PSFalcon v2.2.5_
