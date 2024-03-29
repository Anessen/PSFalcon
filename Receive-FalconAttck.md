# Receive-FalconAttck
## SYNOPSIS
Download Mitre ATT&CK information for an actor
## DESCRIPTION
Requires 'Actors (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Slug|String|Actor identifier ('slug')||||||
|Format|String|Export format|||`csv`<BR>`json`|||
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconAttck [-Path] <String> [-Slug] <String> [-Format] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/entities/mitre-reports/v1
```
### falconpy
[GetMitreReport](https://github.com/CrowdStrike/falconpy/wiki/intel#GetMitreReport)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
