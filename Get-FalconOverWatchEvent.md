# Get-FalconOverWatchEvent
## SYNOPSIS
Retrieve the total number of Falcon OverWatch events across all customers
## DESCRIPTION
Requires 'OverWatch Dashboard: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
## SYNTAX
```powershell
Get-FalconOverWatchEvent [-Filter] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /overwatch-dashboards/aggregates/ow-events-global-counts/v1
```
### falconpy
[AggregatesOWEventsGlobalCounts](https://github.com/CrowdStrike/falconpy/wiki/overwatch-dashboard#AggregatesOWEventsGlobalCounts)
## USAGE
### Getting the total number of Falcon OverWatch events that occurred across all customers
```powershell
Get-FalconOverWatchEvent -Filter "total_count:>1"
```

_2023-04-25: PSFalcon v2.2.5_
