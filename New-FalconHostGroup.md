# New-FalconHostGroup
## SYNOPSIS
Create host groups
## DESCRIPTION
Requires 'Host groups: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of host groups to create in a single request||||X||
|GroupType|String|Host group type|||`dynamic`<BR>`static`<BR>`staticByID`|||
|Name|String|Host group name||||||
|Description|String|Host group description||||||
|AssignmentRule|String|Assignment rule for 'dynamic' host groups||||||
## SYNTAX
```powershell
New-FalconHostGroup [-GroupType] <String> [-Name] <String> [[-Description] <String>] [[-AssignmentRule] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconHostGroup -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /devices/entities/host-groups/v1
```
### falconpy
[createHostGroups](https://github.com/CrowdStrike/falconpy/wiki/host-group#createHostGroups)
## USAGE
### Creating a dynamic host group with a single assignment rule
```powershell
New-FalconHostGroup -GroupType dynamic -Name 'Dynamic group' -Description 'example group' -AssignmentRule "tags:'FalconGroupingTags/example_tag'"
```
### Creating a dynamic host group with multiple assignment rules
```powershell
New-FalconHostGroup -GroupType dynamic -Name 'Dynamic group' -Description 'example group' -AssignmentRule "tags:'FalconGroupingTags/example_tag'+hostname:'CS-WIN10'"
```
### Creating a static host group
```powershell
New-FalconHostGroup -GroupType static -Name 'Test Group 45' -Description 'A demo group'
```
_See [Create a host group and add a list of devices by hostname](https://github.com/CrowdStrike/psfalcon/blob/master/samples/host_groups/create-a-host-group-and-add-a-list-of-devices-by-hostname.ps1)._

_2023-04-25: PSFalcon v2.2.5_
