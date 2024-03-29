# Get-FalconSensorUpdatePolicyMember
## SYNOPSIS
Search for members of Sensor Update policies
## DESCRIPTION
Requires 'Sensor update policies: Read'.
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
Get-FalconSensorUpdatePolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSensorUpdatePolicyMember [[-Id] <String>] [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/sensor-update-members/v1
GET /policy/queries/sensor-update-members/v1
```
### falconpy
[querySensorUpdatePolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#querySensorUpdatePolicyMembers)<BR>[queryCombinedSensorUpdatePolicyMembers](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#queryCombinedSensorUpdatePolicyMembers)
## USAGE
### List IDs of Sensor Update policy members
```powershell
Get-FalconSensorUpdatePolicyMember -Id <id> [-All]
```

_2023-04-25: PSFalcon v2.2.5_
