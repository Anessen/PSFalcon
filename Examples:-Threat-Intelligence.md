## Search for data about actors

### Search for actors

```powershell
Get-FalconActor -Filter "target_countries:'united states'+target_countries:'canada'+target_industries:'government'"
```

### Get information about specific actors

```powershell
Get-FalconActor -Ids <id>, <id>
```

### Search for information about actors

```powershell
Get-FalconActor -Filter "target_countries:'united states'+target_countries:'canada'+target_industries:'government'" -Limit 1 -Detailed
```

## Query for various types of indicators

### Search for indicators

```powershell
Get-FalconIndicator -Filter "type:'domain'" [-Detailed]
```

### Get information about specific indicators

```powershell
Get-FalconIndicator -Ids <id>, <id>
```

### Search for information about indicators

```powershell
Get-FalconIndicator -Filter "last_updated:>=1427846400" -Sort "last_updated|asc" -Detailed
```

## Query CrowdStrike intelligence publications

### Search for reports

```powershell
Get-FalconReport -Filter "target_countries:'united states'+target_industries:'government'"
```

### Get information about specific reports

```powershell
Get-FalconReport -Ids <id>, <id>
```

### Search for information about reports

```powershell
Get-FalconReport -Filter "target_countries:'afghanistan'" -Limit 1 -Detailed
```
## Download rules to use in other tools

### Download the latest rule set

```powershell
Receive-FalconRule -Type yara-master -Path $pwd\yara-master.zip
```

### Search for a rule set

```powershell
Get-FalconRule -Filter "type=yara-master&min_created_date_date=1509494400" -Limit 3
```

### Get information about a specific rule set

```powershell
Get-FalconRule -Ids <id>, <id>
```

### Download a specific rule set

```powershell
Receive-FalconRule -Id <id> -Path $pwd\rules.zip
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/72/intel-apis)