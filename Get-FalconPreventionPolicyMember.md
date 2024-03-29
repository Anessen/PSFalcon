# Get-FalconPreventionPolicyMember
## SYNOPSIS
Search for members of Prevention policies
## DESCRIPTION
Requires 'Prevention Policies: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Policy identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Offset|Int32|Position to begin retrieving results||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconPreventionPolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconPreventionPolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/prevention-members/v1
GET /policy/queries/prevention-members/v1
```
### falconpy
[queryPreventionPolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#queryPreventionPolicyMembers)<BR>[queryCombinedPreventionPolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#queryCombinedPreventionPolicyMembers)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
