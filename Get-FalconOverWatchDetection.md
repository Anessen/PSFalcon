# Get-FalconOverWatchDetection
## SYNOPSIS
Retrieve the total number of Falcon OverWatch detections across all customers
## DESCRIPTION
Requires 'OverWatch Dashboard: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
## SYNTAX
```powershell
Get-FalconOverWatchDetection [-Filter] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /overwatch-dashboards/aggregates/detections-global-counts/v1
```
### falconpy
[AggregatesDetectionsGlobalCounts](https://github.com/CrowdStrike/falconpy/wiki/overwatch-dashboard#AggregatesDetectionsGlobalCounts)
## USAGE
### Getting the total number of Falcon OverWatch detections for the past 48 hours
```powershell
Get-FalconOverWatchDetection -Filter "detect_time:>'now-48h'"
```

_2023-04-25: PSFalcon v2.2.5_
