# Get-FalconResponsePolicyMember
## SYNOPSIS
Search for members of Real-time Response policies
## DESCRIPTION
Requires 'Response policies: Read'.
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
Get-FalconResponsePolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconResponsePolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/response-members/v1
GET /policy/queries/response-members/v1
```
### falconpy
[queryRTResponsePolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/response-policies#queryRTResponsePolicyMembers)<BR>[queryCombinedRTResponsePolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/response-policies#queryCombinedRTResponsePolicyMembers)
## USAGE
### Show members of a Real Time Response policy
```powershell
Get-FalconResponsePolicyMember -Id <id> [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
