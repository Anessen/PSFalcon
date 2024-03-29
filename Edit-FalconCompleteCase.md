# Edit-FalconCompleteCase
## SYNOPSIS
Modify an existing Falcon Complete case
## DESCRIPTION
Requires 'Message Center: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Content|String|Case content||||||
|DetectionId|String[]|Detection identifier|||||X|
|IncidentId|String[]|Incident identifier|||||X|
|Id|String|Case identifier|||||X|
## SYNTAX
```powershell
Edit-FalconCompleteCase [[-Content] <String>] [[-DetectionId] <String[]>] [[-IncidentId] <String[]>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /message-center/entities/case/v1
```
### falconpy
[UpdateCase](https://github.com/CrowdStrike/falconpy/wiki/message-center#UpdateCase)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
