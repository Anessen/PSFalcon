# Set-FalconFileVantagePrecedence
## SYNOPSIS
Set FileVantage policy precedence
## DESCRIPTION
All policy identifiers must be supplied in order (including the default policy) to define policy precedence.

Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Type|String|Operating system type|||`Linux`<BR>`Mac`<BR>`Windows`|||
|Id|String[]|Policy identifiers in desired precedence order||||X||
## SYNTAX
```powershell
Set-FalconFileVantagePrecedence [-Type] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/policies-precedence/v1
```
### falconpy
[updatePolicyPrecedence](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updatePolicyPrecedence)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
