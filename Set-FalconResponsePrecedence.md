# Set-FalconResponsePrecedence
## SYNOPSIS
Set Real-time Response policy precedence
## DESCRIPTION
All policy identifiers must be supplied in order (with the exception of the 'platform_default' policy) to define
policy precedence.

Requires 'Response policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Id|String[]|Policy identifiers in desired precedence order||||||
## SYNTAX
```powershell
Set-FalconResponsePrecedence [-PlatformName] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/response-precedence/v1
```
### falconpy
[setRTResponsePoliciesPrecedence](https://github.com/CrowdStrike/falconpy/wiki/response-policies#setRTResponsePoliciesPrecedence)
## USAGE
### Set policy precedence
**NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in precedence order.
```powershell
Set-FalconResponsePrecedence -PlatformName Windows -Id <id1>, <id2>, <id3>, <id4>
```

_2023-04-25: PSFalcon v2.2.5_
