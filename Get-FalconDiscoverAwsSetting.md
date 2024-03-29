# Get-FalconDiscoverAwsSetting
## SYNOPSIS
Retrieve global settings for Cloud AWS accounts in Falcon Discover
## DESCRIPTION
Requires 'AWS accounts: Read'.
## SYNTAX
```powershell
Get-FalconDiscoverAwsSetting [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-aws/combined/settings/v1
```
### falconpy
[GetAWSSettings](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#GetAWSSettings)
## USAGE
```powershell
Get-FalconDiscoverAwsSetting
```

_2023-04-25: PSFalcon v2.2.5_
