# Edit-FalconDetection
## SYNOPSIS
Modify detections
## DESCRIPTION
Requires 'Detections: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Comment|String|Detection comment||||||
|ShowInUi|Boolean|Visible within the Falcon UI [default: $true]||||||
|Status|String|Detection status|||`new`<BR>`in_progress`<BR>`true_positive`<BR>`false_positive`<BR>`closed`<BR>`reopened`||X|
|AssignedToUuid|String|User identifier for assignment|||||X|
|Id|String[]|Detection identifier||||X|X|
## SYNTAX
```powershell
Edit-FalconDetection [[-Comment] <String>] [[-ShowInUi] <Boolean>] [[-Status] <String>] [[-AssignedToUuid] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /detects/entities/detects/v2
```
### falconpy
[UpdateDetectsByIdsV2](https://github.com/CrowdStrike/falconpy/wiki/detects#UpdateDetectsByIdsV2)
## USAGE
**NOTE**: `Edit-FalconDetection` will automatically group requests in batches of 1,000 detections \(the API limit\).
### Modify the status of multiple detections
```powershell
Edit-FalconDetection -Id <id>, <id> -Status new
```
### Hide detections from the UI
**WARNING**: Hiding detections is not reversible!
```powershell
Edit-FalconDetection -Id <id>, <id> -ShowInUi $false
```

_See [Hide detections involving a specific file](https://github.com/CrowdStrike/psfalcon/blob/master/samples/detections/hide-detections-involving-a-specific-file.ps1)_.

_2023-04-25: PSFalcon v2.2.5_
