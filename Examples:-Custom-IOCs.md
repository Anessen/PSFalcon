### Finding domain and IPv4 IOCs

```powershell
Get-FalconIOC -Type domain, ipv4 [-Detailed]
```

### Retrieve detail on an IOC based on the associated domain name
```powershell
Get-FalconIOC -Ids domain:crowdstrike.com
```

### Create a custom IOC
```powershell
New-FalconIOC -Type domain -Value example.com -Description description -ShareLevel red -Source source -Policy detect -ExpirationDays 30
```

### Get the device count for a custom IOC
```powershell
Get-FalconIOCTotal -Type domain -Value crowdstrike.com
```

### List the Host identifiers that have observed a custom IOC
```powershell
Get-FalconIOCHost -Type domain -Value crowdstrike.com
```

### Find the process identifier of an IOC found on a host
```powershell
Get-FalconIOCProcess -Type domain -Value crowdstrike.com -HostId <id> [-Detailed]
```

### Investigate a process
```powershell
Get-FalconProcess -Ids <id>, <id>
```

[CrowdStrike API Link](https://falcon.crowdstrike.com/support/documentation/88/custom-ioc-apis)