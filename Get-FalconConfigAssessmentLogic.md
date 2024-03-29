# Get-FalconConfigAssessmentLogic
## SYNOPSIS
Retrieve detailed evaluation logic from a configuration assessment
## DESCRIPTION
Requires 'Configuration Assessment: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Evaluation logic identifier||||X|X|
## SYNTAX
```powershell
Get-FalconConfigAssessmentLogic [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /configuration-assessment/entities/evaluation-logic/v1
```
### falconpy
[getEvaluationLogicMixin0](https://github.com/CrowdStrike/falconpy/wiki/spotlight-evaluation-logic#getEvaluationLogicMixin0)
## USAGE

_2023-09-14: PSFalcon v2.2.6_
