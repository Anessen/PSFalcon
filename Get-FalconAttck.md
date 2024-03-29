# Get-FalconAttck
## SYNOPSIS
Search for Mitre ATT&CK tactic and technique information related to specific actors
## DESCRIPTION
Requires 'Actors (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Tactic and technique identifier, by actor||||X||
|Slug|String|Actor identifier ('slug')||||||
## SYNTAX
```powershell
Get-FalconAttck [-Slug] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconAttck -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/queries/mitre/v1
POST /intel/entities/mitre/v1
```
### falconpy
[QueryMitreAttacks](https://github.com/CrowdStrike/falconpy/wiki/intel#QueryMitreAttacks)<BR>[PostMitreAttacks](https://github.com/CrowdStrike/falconpy/wiki/intel#PostMitreAttacks)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
