# Get-FalconFileVantageRuleGroup
## SYNOPSIS
Search for FileVantage rule groups
## DESCRIPTION
Requires 'Falcon FileVantage: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|FileVantage rule group identifier||||X|X|
|Type|String|Rule group type|||`LinuxFiles`<BR>`MacFiles`<BR>`WindowsFiles`<BR>`WindowsRegistry`|||
|Sort|String|Property and direction to sort results|||`created_timestamp\|asc`<BR>`created_timestamp\|desc`<BR>`modified_timestamp\|asc`<BR>`modified_timestamp\|desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconFileVantageRuleGroup [-Type] <String> [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFileVantageRuleGroup -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /filevantage/entities/rule-groups/v1
GET /filevantage/queries/rule-groups/v1
```
### falconpy
[queryRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#queryRuleGroups)<BR>[getRuleGroups](https://github.com/CrowdStrike/falconpy/wiki/filevantage#getRuleGroups)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
