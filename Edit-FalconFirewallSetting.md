# Edit-FalconFirewallSetting
## SYNOPSIS
Modify Falcon Firewall Management policy settings
## DESCRIPTION
All fields are required to modify policy settings. PSFalcon adds missing values automatically using data from
your existing policy.

If adding or removing rule groups, all rule groups must be supplied in precedence order.

Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PlatformId|String|Operating System platform identifier|||`0`<BR>`1`||X|
|Enforce|Boolean|Policy enforcement status|||||X|
|RuleGroupId|String[]|Rule group identifier|||||X|
|DefaultInbound|String|Default action for inbound traffic|||`ALLOW`<BR>`DENY`||X|
|DefaultOutbound|String|Default action for outbound traffic|||`ALLOW`<BR>`DENY`||X|
|MonitorMode|Boolean|Override all block rules and enable monitoring|||||X|
|LocalLogging|Boolean|Enable local logging of firewall events|||||X|
|Id|String|Policy identifier|||||X|
## SYNTAX
```powershell
Edit-FalconFirewallSetting [[-PlatformId] <String>] [[-Enforce] <Boolean>] [[-RuleGroupId] <String[]>] [[-DefaultInbound] <String>] [[-DefaultOutbound] <String>] [[-MonitorMode] <Boolean>] [[-LocalLogging] <Boolean>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PUT /fwmgr/entities/policies/v2
```
### falconpy
[update_policy_container](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#update_policy_container)
## USAGE
### Modify firewall policy settings
```powershell
Edit-FalconFirewallSetting -PolicyId <id> -Enforce $true -DefaultInbound DENY -DefaultOutbound ALLOW
```

_2023-04-25: PSFalcon v2.2.5_
