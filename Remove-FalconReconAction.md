# Remove-FalconReconAction
## SYNOPSIS
Remove an action from a Falcon Intelligence Recon monitoring rule
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Action identifier||||X|X|
## SYNTAX
```powershell
Remove-FalconReconAction [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
DELETE /recon/entities/actions/v1
```
### falconpy
[DeleteActionV1](https://github.com/CrowdStrike/falconpy/wiki/recon#DeleteActionV1)
## USAGE
### Deleting email notifications for a monitoring rule
```powershell
Remove-FalconReconAction -Id <id>
```

_2023-04-25: PSFalcon v2.2.5_
