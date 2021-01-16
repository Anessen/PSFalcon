### Perform a simple YARA search for a specific hash

**NOTE**: PSFalcon has a custom command named `Search-FalconMalQueryHash` which will run a simple YARA-based hash search to find a SHA256 value.

```powershell
Search-FalconMalQueryHash -Sha256 <sha256>
```

### Schedule a hunt

```powershell
Invoke-FalconMalQuery -FilterFiletypes pe32 -MaxSize 1200KB -FilterMeta sha256, label, family -YaraRule "rule CrowdStrike_16142_01 : wiper { strings: $ = { 41 61 43 63 64 44 65 46 66 47 68 69 4B 4C 6C 4D 6D 6E 4E 6F 4F 70 50 72 52 73 53 54 74 55 75 56 76 77 57 78 79 5A 7A 33 32 2E 5C 45 62 67 6A 48 49 20 5F 59 51 42 3A 22 2F 40 } condition: all of them and filesize < 800KB }"
```

### Perform an exact search

```powershell
Invoke-FalconMalQuery -FilterMeta sha256, type, size -FilterFiletypes pe32, pe64 -MaxSize 1200KB -MinDate 2017/01/01 -Limit 20 -Type hex -Value 8948208b480833ca33f989502489482889782c8bd7
```

### Perform a fuzzy search

```powershell
Invoke-FalconMalQuery -Limit 3 -Type ascii -Value ".8@bVn7r&k" -Fuzzy
```

### Check the status of a search

```powershell
Get-FalconMalQuery -Ids <id>, <id>
```

### Retrieve MalQuery sample metadata

```powershell
Get-FalconMalQuerySample -Ids <sha256>, <sha256>
```

### Download a MalQuery sample

```powershell
Receive-FalconMalQuerySample -Id <sha256> -Path $pwd\infected.exe
```

### Download an archive of multiple MalQuery samples

```powershell
$Request = Group-FalconMalQuerySample -Samples <sha256>, <sha256>
Receive-FalconMalQuerySample -Id $Request.reqid -Path .\infected.zip
```

### Check your MalQuery quota

```powershell
Get-FalconMalQueryQuota
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/113/malquery-apis)