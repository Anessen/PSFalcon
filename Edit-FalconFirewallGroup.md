# Edit-FalconFirewallGroup
## SYNOPSIS
Modify Falcon Firewall Management rule groups
## DESCRIPTION
All fields (plus 'rulegroup_version' and 'tracking') are required when making a rule group change. PSFalcon adds
missing values automatically using data from your existing rule group.

'DiffOperation' array objects must contain 'op', 'path' and 'value' properties. Accepted 'op' values are 'add',
'remove' and 'replace'.

When adding a rule to a rule group,the required rule fields must be included along with a 'temp_id' (in both the
rule properties and in precedence order within 'rule_ids') to establish proper placement of the rule within the
rule group. Simlarly, the value 'null' must be placed within 'rule_versions' in precedence order.

Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|DiffOperation|Object[]|An array of hashtables containing rule or rule group changes||||||
|Comment|String|Audit log comment||||||
|RuleId|String[]|Firewall rule 'family' value(s) from the existing rule group [or 'temp_id' for each new rule]||||||
|RuleVersion|Int32[]|Firewall rule version value(s) from the existing rule group [or 'null' for each new rule]||||||
|Id|String|Rule group identifier||||X|X|
|Validate|Switch|Toggle to perform validation, instead of modifying rule group||||||
## SYNTAX
```powershell
Edit-FalconFirewallGroup [-DiffOperation] <Object[]> [[-Comment] <String>] [[-RuleId] <String[]>] [[-RuleVersion] <Int32[]>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconFirewallGroup [-DiffOperation] <Object[]> [[-Comment] <String>] [[-RuleId] <String[]>] [[-RuleVersion] <Int32[]>] [-Id] <String> -Validate [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /fwmgr/entities/rule-groups/v1
PATCH /fwmgr/entities/rule-groups/validation/v1
```
### falconpy
[update_rule_group](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#update_rule_group)<BR>[update_rule_group_validation](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#update_rule_group_validation)
## USAGE
### Enable a firewall rule group
```powershell
Edit-FalconFirewallGroup -Id <id> -DiffOperation @{ op = 'replace'; path = '/enabled'; value = $true }
```
### Add a rule at the beginning of a firewall rule group
```powershell
$DiffOperation = @(
    @{
        op = 'add'
        path = '/rules/0'
        value = @{
            temp_id = '1'
            name = 'First rule in a group'
            description = 'Example'
            platform_ids = @('0')
            enabled = $false
            action = 'ALLOW'
            direction = 'IN'
            address_family = 'NONE'
            protocol = '6'
            fields = @(
                @{
                    name = 'network_location'
                    type = 'set'
                    values = @( 'ANY' )
                }
            )
            local_address = @(@{ address = '*'; netmask = 0 })
            remote_address = @(@{ address = '*'; netmask = 0 })
        }
    }
)
$Group = Get-FalconFirewallGroup -Id <id>
$Rule = Get-FalconFirewallRule -Id $Group.rule_ids
$RuleId = @('1') + $Group.rule_ids
$RuleVersion = @('null') + $Rule.version
Edit-FalconFirewallGroup -Id $Group.id -DiffOperation $DiffOperation -RuleId $RuleId -RuleVersion $RuleVersion
```
### Rename a firewall group
```powershell
Edit-FalconFirewallGroup -Id <id> -DiffOperation @{ op = 'replace'; path = '/name'; value = 'my new name' }
```
### Rename a firewall rule inside of a group
```powershell
$Group = Get-FalconFirewallGroup -Filter "name:'my_group'" -Detailed
$Rule = Get-FalconFirewallRule -Id $Group.rule_ids
$Family = ($Rule | Where-Object { $_.name -eq 'my target rule' }).family
$Index = $Group.rule_ids.IndexOf($Family)
Edit-FalconFirewallGroup -Id $Group.id -DiffOperation @{ op = 'replace'; path = "/rules/$Index/name"; value = 'my new rule name' }
```

_2023-04-25: PSFalcon v2.2.5_
