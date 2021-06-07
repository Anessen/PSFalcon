## Managing firewall rule groups
### Creating firewall rule groups
The `-Rules` parameter accepts a PowerShell array of rule objects which are converted to Json before submission.
```powershell
$Rules = @(
    @{
        name = 'Block IP'
        description = 'Block outbound to example.com IP address'
        platform_ids = @( "0" )
        enabled = $true
        action = "DENY"
        direction = "OUT"
        address_family = "IP4"
        protocol = "*"
        fields = @(
            @{
                name = "network_location"
                type = "set"
                values = @( "ANY" )
            }
        )
        local_address = @(
            @{
                address = "*"
                netmask = 0
            }
        )
        remote_address = @(
            @{
                address = "93.184.216.34"
                netmask = 32
            }
        )
    }
)
New-FalconFirewallGroup -Name 'test rule group' -Enabled $true -Description 'describing a rule group' -Rules $Rules
```
### Finding rule IDs in a firewall rule group
```powershell
Get-FalconFirewallGroup -Ids <id>, <id>
```
### Updating firewall rule groups
```powershell
```
### Deleting firewall rule groups
```powershell
Remove-FalconFirewallGroup -Ids <id>, <id>
```
### Updating firewall rule precedence within a rule group
```powershell
```
## Managing firewall policies
### Creating firewall policies
```powershell
New-FalconFirewallPolicy -PlatformName Windows -Name 'Test Policy' -Description 'Firewall test policy'
```
### Updating firewall policies
```powershell
Edit-FalconFirewallPolicy -Id <id> -Name 'Test Policy 1 Name Changed'
```
### Copying firewall policies
```powershell
New-FalconFirewallPolicy -PlatformName Windows -Name 'Cloned Test Policy' -Description 'Firewall test cloned policy' -CloneId <id>
```
### Enabling firewall policies
```powershell
Invoke-FalconFirewallPolicyAction -Name enable -Id <id>
```
### Disabling firewall policies
```powershell
Invoke-FalconFirewallPolicyAction -Name disable -Id <id>
```
### Deleting firewall policies
```powershell
Remove-FalconFirewallPolicy -Ids <id>, <id>
```
### Managing firewall policy precedence
**NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in desired precedence order.
```powershell
Set-FalconFirewallPrecedence -PlatformName Windows -Ids <id>, <id>
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/107/falcon-firewall-management-apis)._