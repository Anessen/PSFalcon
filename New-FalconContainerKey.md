# New-FalconContainerKey
## SYNOPSIS
Regenerate the API key for Falcon Container Security Docker registry integrations
## DESCRIPTION
Requires 'Kubernetes Protection: Write'.
## SYNTAX
```powershell
New-FalconContainerKey [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /kubernetes-protection/entities/integration/api-key/v1
```
### falconpy
[RegenerateAPIKey](https://github.com/CrowdStrike/falconpy/wiki/kubernetes-protection#RegenerateAPIKey)
## USAGE
### Regenerate API key
```powershell
New-FalconContainerKey
```

_2023-04-25: PSFalcon v2.2.5_
