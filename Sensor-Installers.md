### Find all available sensor installers for Linux

```powershell
Get-FalconInstaller -Filter "platform:'linux'" [-Detailed] [-All]
```

### Find all available sensor installers for a specific OS version

```powershell
Get-FalconInstaller -Filter "os:'Amazon Linux'" [-Detailed] [-All]
```

### Retrieve detailed information about a specific sensor installer

```powershell
Get-FalconInstaller -Ids <id>
```

### Download a sensor installer

```powershell
Receive-FalconInstaller -Id <id> -Path .\WindowsSensor.exe
```

### Find your Customer ID and Checksum \(CCID\)

```powershell
Get-FalconCCID
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/109/sensor-download-apis)