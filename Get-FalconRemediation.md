# Get-FalconRemediation
## SYNOPSIS
Retrieve detail about remediations specified in a Falcon Spotlight vulnerability
## DESCRIPTION
Requires 'Spotlight vulnerabilities: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|Object[]|Remediation identifier||||X|X|
## SYNTAX
```powershell
Get-FalconRemediation [-Id] <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /spotlight/entities/remediations/v2
```
### falconpy
[getRemediationsV2](https://github.com/CrowdStrike/falconpy/wiki/spotlight-vulnerabilities#getRemediationsV2)
## USAGE
### Get information about specific remediations
```powershell
Get-FalconRemediation -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
