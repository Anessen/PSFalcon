# Edit-FalconFirewallPolicy
## SYNOPSIS
Modify Falcon Firewall Management policies
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to modify in a single request||||X||
|Id|String|Policy identifier||||||
|Name|String|Policy name||||||
|Description|String|Policy description||||||
## SYNTAX
```powershell
Edit-FalconFirewallPolicy [-Id] <String> [[-Name] <String>] [[-Description] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconFirewallPolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/firewall/v1
```
### falconpy
[updateFirewallPolicies](https://github.com/CrowdStrike/falconpy/wiki/firewall-policies#updateFirewallPolicies)
## USAGE
### Updating firewall policies
```powershell
Edit-FalconFirewallPolicy -Id <id> -Name 'Test Policy 1 Name Changed'
```

_2023-04-25: PSFalcon v2.2.5_
