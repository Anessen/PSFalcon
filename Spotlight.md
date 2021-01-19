### Search for vulnerabilities

**NOTE**: The Spotlight API requires the use of a filter when requesting results. If you do not provide one, `Get-FalconVulnerability` defaults to a search for vulnerabilities created within the last 24 hours.

```powershell
Get-FalconVulnerability -Filter "created_timestamp:>'2019-11-25T22:36:12Z'" [-Detailed] [-All]
```

### Get information about specific vulnerabilities

```powershell
Get-FalconVulnerability -Ids <id>, <id>
```

### Get information about specific remediations

```powershell
Get-FalconRemediation -Ids <id>, <id>
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/98/spotlight-apis)