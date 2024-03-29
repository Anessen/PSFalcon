# Get-FalconHorizonAwsLink
## SYNOPSIS
Retrieve a URL to grant Falcon Horizon access in AWS
## DESCRIPTION
Once logging in to the provided link using your AWS administrator credentials, use the 'Create Stack' button to
grant access.

Requires 'CSPM registration: Read'.
## SYNTAX
```powershell
Get-FalconHorizonAwsLink [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-cspm-aws/entities/console-setup-urls/v1
```
### falconpy
[GetCSPMAwsConsoleSetupURLs](https://github.com/CrowdStrike/falconpy/wiki/cspm-registration#GetCSPMAwsConsoleSetupURLs)
## USAGE
### Generate an AWS Cloudformation link
```powershell
$Link = Get-FalconHorizonAwsLink
```
**NOTE**: A link will not be generated if an OrganizationId was included when registering your AWS account.

The link must be visited with your browser to complete the registration process. The PowerShell command `Start-Process` will launch your default browser:
```powershell
Start-Process $Link.url
```

_2023-04-25: PSFalcon v2.2.5_
