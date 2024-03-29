# Get-FalconContainerAssessment
## SYNOPSIS
Retrieve Falcon container image assessment reports
## DESCRIPTION
Requires 'Falcon Container Image: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Registry|String|Container registry||||||
|Repository|String|Container repository||||||
|Tag|String|Container tag||||||
## SYNTAX
```powershell
Get-FalconContainerAssessment [-Registry] <String> [-Repository] <String> [-Tag] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /reports
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
