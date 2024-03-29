# Receive-FalconArtifact
## SYNOPSIS
Download an artifact from a Falcon Intelligence Sandbox report
## DESCRIPTION
Artifact identifier values can be retrieved for specific Falcon Intelligence Sandbox reports using
'Get-FalconReport'.

Requires 'Sandbox (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Id|String|Artifact identifier||||X|X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconArtifact [-Path] <String> [-Id] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /falconx/entities/artifacts/v1
```
### falconpy
[GetArtifacts](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#GetArtifacts)
## USAGE
### Download a strict IOC pack
```powershell
$Report = Get-FalconReport -Id <id>
Receive-FalconArtifact -Id $Report.ioc_report_strict_csv_artifact_id -Path .\ioc_report_strict_csv_artifact_id.csv
```
_See [Get-FalconReport](Get-FalconReport)._

_2023-04-25: PSFalcon v2.2.5_
