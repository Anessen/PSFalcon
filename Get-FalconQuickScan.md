# Get-FalconQuickScan
## SYNOPSIS
Search for Falcon QuickScan results
## DESCRIPTION
Requires 'Quick Scan (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|QuickScan identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconQuickScan [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconQuickScan -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /scanner/entities/scans/v1
GET /scanner/queries/scans/v1
```
### falconpy
[QuerySubmissionsMixin0](https://github.com/CrowdStrike/falconpy/wiki/quick-scan#QuerySubmissionsMixin0)<BR>[GetScans](https://github.com/CrowdStrike/falconpy/wiki/quick-scan#GetScans)
## USAGE
### Search for QuickScans run in the last 7 days
```powershell
Get-FalconQuickScan -Filter "created_timestamp:>'Last 7 days'" [-Detailed]
```
### Retrieve information about a QuickScan
```powershell
Get-FalconQuickScan -Id <id>
```
_See [New-FalconQuickScan](New-FalconQuickScan)._

_2023-04-25: PSFalcon v2.2.5_
