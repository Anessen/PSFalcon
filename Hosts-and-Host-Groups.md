# Finding hosts using filters

## Hosts that match an AWS Instance ID

```powershell
Get-FalconHost -Filter "instance_id:'<instance_id>'" [-Detailed] [-All]
```

## Finding all Windows hosts

```powershell
Get-FalconHost -Filter "platform_name:'Windows'" [-Detailed] [-All]
```

## Finding hosts based on multiple criteria

```powershell
Get-FalconHost -Filter "product_type_desc:'Workstation'+status:'normal'+platform_name:['Windows','Mac']+last_seen:>='2020-07-04'" [-Detailed] [-All]
```

## Retrieving a list of the first 100 hosts in your environment

```powershell
Get-FalconHost [-Detailed]
```

# Getting information about hosts

```powershell
Get-FalconHost -Ids <id>, <id>
```

# Containing and lifting containment on hosts

```powershell
Invoke-FalconHostAction -Name contain -Ids <id>, <id>
```
```powershell
Invoke-FalconHostAction -Name lift_containment -Ids <id>, <id>
```

# Deleting and restoring hosts

```powershell
Invoke-FalconHostAction -Name hide_host -Ids <id>, <id>
```
```powershell
Invoke-FalconHostAction -Name unhide_host -Ids <id>, <id>
```

# Finding hosts that have been deleted

```powershell
Get-FalconHost -Hidden [-Detailed] [-All]
```

# Create a static host group

```powershell
New-FalconHostGroup -GroupType static -Name 'Test Group 45' -Description 'A demo group'
```

## Assigning hosts to a static host group

```powershell
Invoke-FalconHostGroupAction -Name add-hosts -Id <id> -HostIds <id>, <id>
```

## Finding host groups

```powershell
Get-FalconHostGroup [-Detailed] [-All]
```

## Deleting host groups

```powershell
Remove-FalconHostGroup -Ids <id>, <id>
```

_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/84/host-and-host-group-management-apis)._