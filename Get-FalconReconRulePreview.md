# Get-FalconReconRulePreview
## SYNOPSIS
Preview Falcon Intelligence Recon monitoring rule notification count and distribution
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Topic|String|Monitoring rule topic||||||
|Filter|String|Monitoring rule filter||||||
## SYNTAX
```powershell
Get-FalconReconRulePreview [-Topic] <String> [-Filter] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /recon/aggregates/rules-preview/GET/v1
```
### falconpy
[PreviewRuleV1](https://github.com/CrowdStrike/falconpy/wiki/recon#PreviewRuleV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
