# Copy-FalconFirewallPolicy
## SYNOPSIS
Duplicate a Falcon Firewall Management policy
## DESCRIPTION
The specified Falcon Firewall Management policy will be duplicated without assigned Host Groups. If a policy
description is not supplied, the description from the existing policy will be used.

Requires 'Firewall management: Read', 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Name for the policy that will be created||||||
|Description|String|Description for the policy that will be created||||||
|Id|String|Identifier of policy to be copied||||X|X|
## SYNTAX
```powershell
Copy-FalconFirewallPolicy [-Name] <String> [[-Description] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
