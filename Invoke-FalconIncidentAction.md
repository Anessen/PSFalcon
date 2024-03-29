# Invoke-FalconIncidentAction
## SYNOPSIS
Perform actions on incidents
## DESCRIPTION
Requires 'Incidents: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add_tag`<BR>`delete_tag`<BR>`unassign`<BR>`update_description`<BR>`update_name`<BR>`update_status`<BR>`update_assigned_to_v2`|||
|Value|String|Value for the chosen action||||||
|UpdateDetects|Boolean|Update status of related 'new' detections||||||
|OverwriteDetects|Boolean|Replace existing status for related detections||||||
|Id|String[]|Incident identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconIncidentAction [-Name] <String> [-Value] <String> [[-UpdateDetects] <Boolean>] [[-OverwriteDetects] <Boolean>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /incidents/entities/incident-actions/v1
```
### falconpy
[PerformIncidentAction](https://github.com/CrowdStrike/falconpy/wiki/incidents#PerformIncidentAction)
## USAGE
### Update the status of multiple incidents
```powershell
Invoke-FalconIncidentAction -Name update_status -Value in_progress -Id <id>, <id>
```
### Updating detection statuses to match incidents
```powershell
Invoke-FalconIncidentAction -Name update_status -Value in_progress -Id <id>, <id> -UpdateDetects $true -OverwriteDetects $true
```

_2023-04-25: PSFalcon v2.2.5_
