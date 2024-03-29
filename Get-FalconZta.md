# Get-FalconZta
## SYNOPSIS
Search for Zero Trust Assessment results
## DESCRIPTION
Requires 'Zero Trust Assessment: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Host identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`score\|desc`<BR>`score\|asc`|||
|Limit|Int32|The maximum records to return|`1`|`1000`||||
|After|String|Pagination token to retrieve the next set of results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconZta [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconZta [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconZta [-Filter] <String> [[-Sort] <String>] [[-Limit] <Int32>] [-After <String>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /zero-trust-assessment/entities/assessments/v1
GET /zero-trust-assessment/entities/audit/v1
GET /zero-trust-assessment/queries/assessments/v1
```
### falconpy
[getAuditV1](https://github.com/CrowdStrike/falconpy/wiki/zero-trust-assessment#getAuditV1)<BR>[getAssessmentV1](https://github.com/CrowdStrike/falconpy/wiki/zero-trust-assessment#getAssessmentV1)<BR>[getAssessmentsByScoreV1](https://github.com/CrowdStrike/falconpy/wiki/zero-trust-assessment#getAssessmentsByScoreV1)
## USAGE
## Retrieving Zero Trust Assessment data by host
```powershell
Get-FalconZta -Id <id>, <id>
```
**NOTE**: The `Include` parameter can be used to append Zero Trust Assessment results to `Get-FalconHost` output.

_See [Get-FalconHost](Get-FalconHost)._
## Retrieving CID aggregate info
```powershell
Get-FalconZta
```

_2023-04-25: PSFalcon v2.2.5_
