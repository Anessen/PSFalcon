# Remove-FalconInstallToken
## SYNOPSIS
Remove installation tokens
## DESCRIPTION
Requires 'Installation tokens: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Installation token identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconInstallToken [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /installation-tokens/entities/tokens/v1
```
### falconpy
[tokens_delete](https://github.com/CrowdStrike/falconpy/wiki/installation-tokens#tokens_delete)
## USAGE
### Delete installation tokens
```powershell
Remove-FalconInstallToken -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
