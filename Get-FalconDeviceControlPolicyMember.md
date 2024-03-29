# Get-FalconDeviceControlPolicyMember
## SYNOPSIS
Search for members of Falcon Device Control policies
## DESCRIPTION
Requires 'Device control policies: Read'.
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
Get-FalconDeviceControlPolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconDeviceControlPolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/device-control-members/v1
GET /policy/queries/device-control-members/v1
```
### falconpy
[queryDeviceControlPolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#queryDeviceControlPolicyMembers)<BR>[queryCombinedDeviceControlPolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#queryCombinedDeviceControlPolicyMembers)
## USAGE
### Show members of a Device Control policy
```powershell
Get-FalconDeviceControlPolicyMember -Id <id> [-Detailed] [-All]
```

_2023-04-25: PSFalcon v2.2.5_
