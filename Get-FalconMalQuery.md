# Get-FalconMalQuery
## SYNOPSIS
Verify the status and results of an asynchronous Falcon MalQuery request, such as a hunt or exact-search
## DESCRIPTION
Requires 'MalQuery: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Request identifier||||X|X|
## SYNTAX
```powershell
Get-FalconMalQuery [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /malquery/entities/requests/v1
```
### falconpy
[GetMalQueryRequestV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#GetMalQueryRequestV1)
## USAGE
### Check the status of a search
```powershell
Get-FalconMalQuery -Id <id>, <id>
```

_2023-04-25: PSFalcon v2.2.5_
