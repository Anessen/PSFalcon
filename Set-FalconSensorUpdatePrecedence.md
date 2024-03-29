# Set-FalconSensorUpdatePrecedence
## SYNOPSIS
Set Sensor Update policy precedence
## DESCRIPTION
All policy identifiers must be supplied in order (with the exception of the 'platform_default' policy) to define
policy precedence.

Requires 'Sensor update policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Id|String[]|Policy identifiers in desired precedence order||||||
## SYNTAX
```powershell
Set-FalconSensorUpdatePrecedence [-PlatformName] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/sensor-update-precedence/v1
```
### falconpy
[setSensorUpdatePoliciesPrecedence](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#setSensorUpdatePoliciesPrecedence)
## USAGE
### Set policy precedence
**NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in precedence order.
```powershell
Set-FalconSensorUpdatePrecedence -PlatformName Windows -Id <id1>, <id2>, <id3>, <id4>
```

_2023-04-25: PSFalcon v2.2.5_
