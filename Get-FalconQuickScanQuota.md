# Get-FalconQuickScanQuota
## SYNOPSIS
Display monthly Falcon QuickScan quota
## DESCRIPTION
Requires 'Quick Scan (Falcon Intelligence): Read'.
## SYNTAX
```powershell
Get-FalconQuickScanQuota [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /scanner/queries/scans/v1
```
### falconpy
[QuerySubmissionsMixin0](https://github.com/CrowdStrike/falconpy/wiki/quick-scan#QuerySubmissionsMixin0)
## USAGE
### Check your QuickScan submission quota
```powershell
Get-FalconQuickScanQuota
```

_2023-04-25: PSFalcon v2.2.5_
