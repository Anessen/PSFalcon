# Get-FalconSensorTag
## SYNOPSIS
Use Real-time Response to display FalconSensorTags assigned to hosts
## DESCRIPTION
Requires 'Hosts: Read' and 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|QueueOffline|Boolean|Add command request to the offline queue||||||
|Id|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Get-FalconSensorTag [[-QueueOffline] <Boolean>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Retrieving Sensor grouping tags
`Get-FalconSensorTag` uses Real-time Response to retrieve tags from the target host(s).
```powershell
Get-FalconSensorTag -Id <id>, <id> -Tag tag1, tag2 [-QueueOffline]
```

_2023-04-25: PSFalcon v2.2.5_
