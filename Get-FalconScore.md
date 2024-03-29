# Get-FalconScore
## SYNOPSIS
Search for CrowdScore values
## DESCRIPTION
Requires 'Incidents: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`timestamp`<BR>`score`||||||
|Sort|String|Property and direction to sort results|||`score.asc`<BR>`score.desc`<BR>`timestamp.asc`<BR>`timestamp.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`2500`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconScore [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /incidents/combined/crowdscores/v1
```
### falconpy
[CrowdScore](https://github.com/CrowdStrike/falconpy/wiki/incidents#CrowdScore)
## USAGE
### Show CrowdScores
```powershell
Get-FalconScore [-All]
```
### Output the highest score for each available day
```powershell
# Retrieve all available scores
$Score = Get-FalconScore -All

# Convert 'timestamp' into local [datetime]
$Score | ForEach-Object { $_.timestamp = [datetime]$_.timestamp }

foreach ($Day in ($Score | ForEach-Object { $_.timestamp.ToString('yyyy-MM-dd') } | Select-Object -Unique |
Sort-Object -Descending)) {
    # Output 'max_score' for each 'date'
    [PSCustomObject]@{
        date = $Day
        max_score = ($Score | Where-Object { $_.timestamp.date -eq $Day }).score | Sort-Object -Descending |
            Select-Object -First 1
    }
}
```

_2023-04-25: PSFalcon v2.2.5_
