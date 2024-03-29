# Set-FalconPreventionPrecedence
## SYNOPSIS
Set Prevention policy precedence
## DESCRIPTION
All policy identifiers must be supplied in order (with the exception of the 'platform_default' policy) to
define policy precedence.

Requires 'Prevention Policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`<BR>`iOS`<BR>`Android`|||
|Id|String[]|Policy identifiers in desired precedence order||||||
## SYNTAX
```powershell
Set-FalconPreventionPrecedence [-PlatformName] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/prevention-precedence/v1
```
### falconpy
[setPreventionPoliciesPrecedence](https://github.com/CrowdStrike/falconpy/wiki/prevention-policy#setPreventionPoliciesPrecedence)
## USAGE
### Set policy precedence **NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in precedence order.
```powershell
Set-FalconPreventionPrecedence -PlatformName Windows -Id <policy_id>, <policy_id>, <policy_id>, <policy_id>
```

_2023-04-25: PSFalcon v2.2.5_
