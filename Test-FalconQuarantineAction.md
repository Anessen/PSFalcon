# Test-FalconQuarantineAction
## SYNOPSIS
Check the number of quarantined files potentially affected by a filter-based action
## DESCRIPTION
Requires 'Quarantined Files: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Filter|String|[Falcon Query Language](Filtering-Results) statement||||||
## SYNTAX
```powershell
Test-FalconQuarantineAction [-Filter] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /quarantine/aggregates/action-update-count/v1
```
### falconpy
[ActionUpdateCount](https://github.com/CrowdStrike/falconpy/wiki/quarantine#ActionUpdateCount)
## USAGE
### Check how quarantined files would be affected by an action
```powershell
Test-FalconQuarantineAction -Filter "device.hostname:'EXAMPLE-PC'"
```
_See [Invoke-FalconQuarantineAction](Invoke-FalconQuarantineAction)._

_2023-04-25: PSFalcon v2.2.5_
