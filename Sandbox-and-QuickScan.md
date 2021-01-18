## Submit a file for analysis

### Upload files for submission

### Submit an uploaded sample for analysis in a sandbox environment

### Check the progress of samples previously submitted for analysis

## Submit an archive file for analysis

## Analyze large volumes of files with Falcon QuickScan

### Submit files to QuickScan

```powershell
New-FalconQuickScan -Samples <sha256>, <sha256>
```

### Search for QuickScans run in the last 7 days

```powershell
Get-FalconQuickScan -Filter "created_timestamp:>'Last 7 days'" [-Detailed]
```

### Retrieve information about a QuickScan

```powershell
Get-FalconQuickScan -Ids <id>
```

## Download reports, IOC packs, and PCAP files

### Download a summary

### Download a report

### Download a strict IOC pack

### Find malware samples or sandbox reports

### Check your submission quota

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/92/falcon-x-apis)