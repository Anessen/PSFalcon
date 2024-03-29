# New-FalconFirewallPolicy
## SYNOPSIS
Create Falcon Firewall Management policies
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to create in a single request||||X||
|Name|String|Policy name||||||
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Description|String|Policy description||||||
## SYNTAX
```powershell
New-FalconFirewallPolicy [-Name] <String> [-PlatformName] <String> [[-Description] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconFirewallPolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/firewall/v1
```
### falconpy
[createFirewallPolicies](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#createFirewallPolicies)
## USAGE
### Creating firewall policies
```powershell
New-FalconFirewallPolicy -PlatformName Windows -Name 'Test Policy' -Description 'Firewall test policy'
```
### Copying firewall policies
```powershell
New-FalconFirewallPolicy -PlatformName Windows -Name 'Cloned Test Policy' -Description 'Firewall test cloned policy' -CloneId <id>
```

_2023-04-25: PSFalcon v2.2.5_
