# Get-FalconFileVantageExclusion
## SYNOPSIS
List scheduled exclusions applied to a FileVantage policy
## DESCRIPTION
Requires 'Falcon FileVantage: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|PolicyId|String|FileVantage policy identifier||||||
|Id|String[]|FileVantage scheduled exclusion identifier||||X|X|
## SYNTAX
```powershell
Get-FalconFileVantageExclusion [-PolicyId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconFileVantageExclusion [-PolicyId] <String> [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /filevantage/entities/policy-scheduled-exclusions/v1
GET /filevantage/queries/policy-scheduled-exclusions/v1
```
### falconpy
[queryScheduledExclusions](https://github.com/CrowdStrike/falconpy/wiki/filevantage#queryScheduledExclusions)<BR>[getScheduledExclusions](https://github.com/CrowdStrike/falconpy/wiki/filevantage#getScheduledExclusions)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
