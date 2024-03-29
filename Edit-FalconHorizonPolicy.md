# Edit-FalconHorizonPolicy
## SYNOPSIS
Modify a Falcon Horizon policy
## DESCRIPTION
Requires 'CSPM registration: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Severity|String|Severity level|||`informational`<BR>`medium`<BR>`high`<BR>`critical`||X|
|Enabled|Boolean|Policy enablement status|||||X|
|Region|String[]|Cloud region|||||X|
|TagExcluded|Boolean|Tag exclusion flag|||||X|
|AccountId|String[]|Account identifier|||||X|
|Id|Int32|Policy identifier|||||X|
## SYNTAX
```powershell
Edit-FalconHorizonPolicy [-Severity] <String> [-Enabled] <Boolean> [[-Region] <String[]>] [[-TagExcluded] <Boolean>] [[-AccountId] <String[]>] -Id <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /settings/entities/policy/v1
```
### falconpy
[UpdateCSPMPolicySettings](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#UpdateCSPMPolicySettings)
## USAGE
### Updating policy settings
```powershell
Edit-FalconHorizonPolicy -PolicyId 20 -Enabled $true -Severity medium
```

_2023-11-27: PSFalcon v2.2.6_
