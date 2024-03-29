# Get-FalconConfigAssessment
## SYNOPSIS
Search for Falcon Spotlight Configuration Assessments
## DESCRIPTION
Requires 'Configuration Assessment: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Facet|String[]|Include additional properties|||`finding.evaluation_logic`<BR>`finding.rule`<BR>`host`|||
|Sort|String|Property and direction to sort results|||`created_timestamp\|asc`<BR>`created_timestamp\|desc`<BR>`updated_timestamp\|asc`<BR>`updated_timestamp\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|After|String|Pagination token to retrieve the next set of results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconConfigAssessment [-Filter] <String> [[-Facet] <String[]>] [[-Sort] <String>] [[-Limit] <Int32>] [-After <String>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /configuration-assessment/combined/assessments/v1
```
### falconpy
[getCombinedAssessmentsQuery](https://github.com/CrowdStrike/falconpy/wiki/configuration-assessment#getCombinedAssessmentsQuery)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
