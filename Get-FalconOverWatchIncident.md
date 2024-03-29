# Get-FalconOverWatchIncident
## SYNOPSIS
Retrieve the total number of Falcon OverWatch incidents across all customers
## DESCRIPTION
Requires 'OverWatch Dashboard: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
## SYNTAX
```powershell
Get-FalconOverWatchIncident [-Filter] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /overwatch-dashboards/aggregates/incidents-global-counts/v1
```
### falconpy
[AggregatesIncidentsGlobalCounts](https://github.com/CrowdStrike/falconpy/wiki/overwatch-dashboard#AggregatesIncidentsGlobalCounts)
## USAGE
### Getting the total number of Falcon OverWatch incidents for the past 48 hours
```powershell
Get-FalconOverWatchIncident -Filter "detect_time:>'now-48h'"
```

_2023-04-25: PSFalcon v2.2.5_
