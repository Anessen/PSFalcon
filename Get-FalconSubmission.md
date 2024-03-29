# Get-FalconSubmission
## SYNOPSIS
Search for Falcon Intelligence Sandbox submissions
## DESCRIPTION
Requires 'Sandbox (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Submission identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconSubmission [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSubmission -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falconx/entities/submissions/v1
GET /falconx/queries/submissions/v1
```
### falconpy
[QuerySubmissions](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#QuerySubmissions)<BR>[GetSubmissions](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#GetSubmissions)
## USAGE
### Check the progress of samples previously submitted for analysis
```powershell
Get-FalconSubmission -Id <id>, <id>
```
_See [New-FalconSubmission](New-FalconSubmission)._

_2023-04-25: PSFalcon v2.2.5_
