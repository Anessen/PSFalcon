# Get-FalconContainerScript
## SYNOPSIS
Return bash scripts for Falcon Cloud Security registration
## DESCRIPTION
Requires 'Kubernetes Protection: Read'.
## SYNTAX
```powershell
Get-FalconContainerScript [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /kubernetes-protection/entities/gen/scripts/v1
```
### falconpy
[GetStaticScripts](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#GetStaticScripts)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
