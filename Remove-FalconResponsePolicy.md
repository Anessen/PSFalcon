# Remove-FalconResponsePolicy
## SYNOPSIS
Remove Real-time Response policies
## DESCRIPTION
Requires 'Response policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconResponsePolicy [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/response/v1
```
### falconpy
[deleteRTResponsePolicies](https://github.com/CrowdStrike/falconpy/wiki/response-policies#deleteRTResponsePolicies)
## USAGE
### Delete a policy
```powershell
Remove-FalconResponsePolicy -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
