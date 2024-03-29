# Remove-FalconIoc
## SYNOPSIS
Remove custom indicators
## DESCRIPTION
Requires 'IOC Manager APIs: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to find indicators for removal||||||
|Comment|String|Audit log comment||||||
|FromParent|Boolean|Inheritance from parent CID||||||
|Id|String[]|Indicator identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconIoc [[-Comment] <String>] [[-FromParent] <Boolean>] [[-Id] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Remove-FalconIoc -Filter <String> [[-Comment] <String>] [[-FromParent] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /iocs/entities/indicators/v1
```
### falconpy
[indicator_delete_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#indicator_delete_v1)
## USAGE
### Deleting indicators by identifier
```powershell
Remove-FalconIoc -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
