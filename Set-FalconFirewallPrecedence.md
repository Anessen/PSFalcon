# Set-FalconFirewallPrecedence
## SYNOPSIS
Set Falcon Firewall Management policy precedence
## DESCRIPTION
All policy identifiers must be supplied in order (with the exception of the 'platform_default' policy) to define
policy precedence.

Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Id|String[]|Policy identifiers in desired precedence order||||||
## SYNTAX
```powershell
Set-FalconFirewallPrecedence [-PlatformName] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/firewall-precedence/v1
```
### falconpy
[setFirewallPoliciesPrecedence](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#setFirewallPoliciesPrecedence)
## USAGE
### Managing firewall policy precedence
**NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in desired precedence order.
```powershell
Set-FalconFirewallPrecedence -PlatformName Windows -Id <id1>, <id2>, <id3>, <id4>
```

_2023-04-25: PSFalcon v2.2.5_
