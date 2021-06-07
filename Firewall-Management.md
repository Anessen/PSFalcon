## Managing firewall rule groups
### Creating firewall rule groups
Firewall rules can be added at the time of group creation, or added after the group is created using `Edit-FalconFirewallGroup`. The `-Rules` parameter accepts a PowerShell array of rule objects which are converted to Json before submission.
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
Edit-FalconFirewallGroup -PolicyId <id> 
```
### Deleting firewall rule groups
```powershell
Remove-FalconFirewallGroup -Ids <id>, <id>
```
### Updating firewall rule precedence within a rule group
```powershell
```
## Managing firewall policies
```powershell
```
### Creating firewall policies
```powershell
```
### Updating firewall policies
```powershell
```
### Copying firewall policies
```powershell
```
### Enabling firewall policies
```powershell
```
### Disabling firewall policies
```powershell
```
### Deleting firewall policies
```powershell
```
### Managing firewall policy precedence
```powershell
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/107/falcon-firewall-management-apis)._