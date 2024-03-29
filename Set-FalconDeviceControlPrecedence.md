# Set-FalconDeviceControlPrecedence
## SYNOPSIS
Set Falcon Device Control policy precedence
## DESCRIPTION
All policy identifiers must be supplied in order (with the exception of the 'platform_default' policy) to define
policy precedence.

Requires 'Device control policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Id|String[]|Policy identifiers in desired precedence order||||||
## SYNTAX
```powershell
Set-FalconDeviceControlPrecedence [-PlatformName] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/device-control-precedence/v1
```
### falconpy
[setDeviceControlPoliciesPrecedence](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#setDeviceControlPoliciesPrecedence)
## USAGE
### Set policy precedence
**NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in precedence order.
```powershell
Set-FalconDeviceControlPrecedence -PlatformName Windows -Id <id1>, <id2>, <id3>, <id4>
```

_2023-04-25: PSFalcon v2.2.5_
