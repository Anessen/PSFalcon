# Get-FalconMalQueryQuota
## SYNOPSIS
Retrieve Falcon MalQuery search and download quotas
## DESCRIPTION
Requires 'MalQuery: Read'.
## SYNTAX
```powershell
Get-FalconMalQueryQuota [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /malquery/aggregates/quotas/v1
```
### falconpy
[GetMalQueryQuotasV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#GetMalQueryQuotasV1)
## USAGE
### Check your MalQuery quota
```powershell
Get-FalconMalQueryQuota
```

_2023-04-25: PSFalcon v2.2.5_
