# New-FalconFirewallGroup
## SYNOPSIS
Create Falcon Firewall Management rule groups
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Rule group name|||||X|
|Enabled|Boolean|Rule group status|||||X|
|Description|String|Rule group description|||||X|
|Rule|Object[]|Firewall rules|||||X|
|Comment|String|Audit log comment|||||X|
|Library|String|Clone default Firewall rules||||||
|CloneId|String|Clone an existing rule group||||||
|Platform|String|Operating system platform [default: 0 (Windows)]|||||X|
|Validate|Switch|Toggle to perform validation, instead of creating rule group||||||
## SYNTAX
```powershell
New-FalconFirewallGroup [-Name] <String> [-Enabled] <Boolean> [[-Description] <String>] [[-Rule] <Object[]>] [[-Comment] <String>] [[-Library] <String>] [[-CloneId] <String>] [[-Platform] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconFirewallGroup [-Name] <String> [-Enabled] <Boolean> [[-Description] <String>] [[-Rule] <Object[]>] [[-Comment] <String>] [[-Library] <String>] [[-CloneId] <String>] [[-Platform] <String>] -Validate [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /fwmgr/entities/rule-groups/v1
POST /fwmgr/entities/rule-groups/validation/v1
```
### falconpy
[create_rule_group](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#create_rule_group)<BR>[create_rule_group_validation](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#create_rule_group_validation)
## USAGE
### Creating firewall rule groups
The `Rules` parameter accepts a PowerShell array of rule objects which are converted to Json before submission.
```powershell
$Rule = @(
    @{
        name = 'Block IP'
        description = 'Block outbound to example.com IP address'
        platform_ids = @( '0' )
        enabled = $true
        action = 'DENY'
        direction = 'OUT'
        address_family = 'IP4'
        protocol = '*'
        fields = @(
            @{
                name = 'network_location'
                type = 'set'
                values = @( 'ANY' )
            }
        )
        local_address = @(@{ address = '*'; netmask = 0 })
        remote_address = @(@{ address = '93.184.216.34'; netmask = 32 })
    }
)
New-FalconFirewallGroup -Name 'test rule group' -Enabled $true -Description 'describing a rule group' -Rule $Rule
```

_2023-04-25: PSFalcon v2.2.5_
