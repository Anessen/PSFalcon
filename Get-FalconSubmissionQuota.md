# Get-FalconSubmissionQuota
## SYNOPSIS
Retrieve monthly Falcon Intelligence Sandbox submission quota
## DESCRIPTION
Requires 'Sandbox (Falcon Intelligence): Read'.
## SYNTAX
```powershell
Get-FalconSubmissionQuota [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falconx/queries/submissions/v1
```
### falconpy
[QuerySubmissions](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#QuerySubmissions)
## USAGE
### Check your Sandbox submission quota
```powershell
Get-FalconSubmissionQuota
```

_2023-04-25: PSFalcon v2.2.5_
