## Submit a file for analysis

TO_DO

### Upload files for submission

TO_DO

### Submit an uploaded sample for analysis in a sandbox environment

TO_DO

### Check the progress of samples previously submitted for analysis

TO_DO

## Submit an archive file for analysis

TO_DO

## Analyze large volumes of files with Falcon QuickScan

TO_DO

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

TO_DO

### Download a report

TO_DO

### Download a strict IOC pack

TO_DO

### Find malware samples or sandbox reports

TO_DO

### Check your submission quota

TO_DO

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/92/falcon-x-apis)