# Remove-FalconContainerImage
## SYNOPSIS
Remove a Falcon container image
## DESCRIPTION
Requires 'Falcon Container Image: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|Object|Container image identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconContainerImage [-Id] <Object> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /images/{id}
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
