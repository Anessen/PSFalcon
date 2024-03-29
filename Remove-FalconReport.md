# Remove-FalconReport
## SYNOPSIS
Remove a Falcon Intelligence Sandbox report
## DESCRIPTION
Requires 'Sandbox (Falcon Intelligence): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Report identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconReport [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /falconx/entities/reports/v1
```
### falconpy
[DeleteReport](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#DeleteReport)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
