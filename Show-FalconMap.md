# Show-FalconMap
## SYNOPSIS
Display indicators on the Falcon Intelligence Indicator Map
## DESCRIPTION
Your default web browser will be used to view the Indicator Map.

Show-FalconMap will accept domains, SHA256 hashes, IP addresses and URLs. Invalid indicator values are ignored.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Indicator|String[]|Indicator to display on the Indicator map||||X||
## SYNTAX
```powershell
Show-FalconMap [-Indicator] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Map indicators
```powershell
Get-FalconIndicator -Filter "type:'hash_sha256'" -Limit 5 | Show-FalconMap
```
```powershell
Show-FalconMap -Indicator www.google.com, 8.8.8.8
```

_2023-04-25: PSFalcon v2.2.5_
