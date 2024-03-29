# Invoke-FalconAlertAction
## SYNOPSIS
Perform actions on alerts
## DESCRIPTION
Requires 'Alerts: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add_tag`<BR>`append_comment`<BR>`assign_to_name`<BR>`assign_to_user_id`<BR>`assign_to_uuid`<BR>`remove_tag`<BR>`remove_tags_by_prefix`<BR>`show_in_ui`<BR>`unassign`<BR>`update_status`|||
|Value|String|Value for the chosen action||||||
|Id|String[]|Alert identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconAlertAction [-Name] <String> [[-Value] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /alerts/entities/alerts/v3
```
### falconpy
[PatchEntitiesAlertsV3](https://github.com/CrowdStrike/falconpy/wiki/alerts#PatchEntitiesAlertsV3)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
