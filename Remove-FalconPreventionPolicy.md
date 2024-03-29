# Remove-FalconPreventionPolicy
## SYNOPSIS
Remove Prevention policies
## DESCRIPTION
Requires 'Prevention Policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconPreventionPolicy [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /policy/entities/prevention/v1
```
### falconpy
[deletePreventionPolicies](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#deletePreventionPolicies)
## USAGE
### Delete prevention policies
```powershell
Remove-FalconPreventionPolicy -Id <id>, <id>
```
```powershell
Get-FalconPreventionPolicy -Filter "name:'my_policy'" | Invoke-FalconPreventionPolicyAction -Name disable | Remove-FalconPreventionPolicy
```

_2023-04-25: PSFalcon v2.2.5_
