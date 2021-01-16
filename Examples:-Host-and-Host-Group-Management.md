## Finding hosts using filters

### Hosts that match an AWS Instance ID

```powershell
Get-FalconHost -Filter "instance_id:'<instance_id>'" [-All]
```

### Finding all Windows hosts

```powershell
Get-FalconHost -Filter "platform_name:'Windows'" [-All]
```

### Finding hosts based on multiple criteria

```powershell
Get-FalconHost -Filter "product_type_desc:'Workstation'+status:'normal'+platform_name:['Windows','Mac']+last_seen:>='2020-07-04'" [-All]
```

### Retrieving a list of the first 100 hosts in your environment

```powershell
Get-FalconHost
```

### Getting information about hosts

```powershell
Get-FalconHost -Ids <id>, <id>
```

### Containing and lifting containment on hosts

```powershell
Invoke-FalconHostAction -ActionName contain -Ids <id>, <id>
```
```powershell
Invoke-FalconHostAction -ActionName lift_containment -Ids <id>, <id>
```

### Deleting and restoring hosts

```powershell
Invoke-FalconHostAction -ActionName hide_host -Ids <id>, <id>
```
```powershell
Invoke-FalconHostAction -ActionName unhide_host -Ids <id>, <id>
```

### Finding hosts that have been deleted

```powershell
Get-FalconHost -Hidden [-Detailed]
```

### Create a static host group

```powershell
New-FalconHostGroup -GroupType static -Name 'Test Group 45' -Description 'A demo group'
```

### Assigning hosts to a static host group

```powershell
Invoke-FalconHostGroupAction -ActionName add-hosts -Id <id> -HostIds <id>, <id>
```

### Finding host groups

```powershell
Get-FalconHostGroup [-Detailed]
```

### Deleting host groups

```powershell
Remove-FalconHostGroup -Ids <id>, <id>
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/84/host-and-host-group-management-apis)