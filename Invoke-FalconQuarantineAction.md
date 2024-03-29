# Invoke-FalconQuarantineAction
## SYNOPSIS
Perform actions on quarantined files
## DESCRIPTION
Requires 'Quarantined Files: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Action|String|Action to perform|||`release`<BR>`unrelease`<BR>`delete`|||
|Filter|String|[Falcon Query Language](Filtering-Results) statement||||||
|Query|String|Match phrase prefix||||||
|Comment|String|Audit log comment||||||
|Id|String[]|Quarantined file identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconQuarantineAction [-Action] <String> [[-Comment] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconQuarantineAction [-Action] <String> -Filter <String> [[-Query] <String>] [[-Comment] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /quarantine/entities/quarantined-files/v1
PATCH /quarantine/queries/quarantined-files/v1
```
### falconpy
[UpdateQuarantinedDetectsByIds](https://github.com/CrowdStrike/falconpy/wiki/quarantine#UpdateQuarantinedDetectsByIds)<BR>[UpdateQfByQuery](https://github.com/CrowdStrike/falconpy/wiki/quarantine#UpdateQfByQuery)
## USAGE
### Delete specific quarantined files
```powershell
Invoke-FalconQuarantineAction -Action delete -Id <id>, <id>
```
### Release quarantined files using a filtered search
```powershell
Invoke-FalconQuarantineAction -Action release -Filter "device.hostname:'EXAMPLE-PC'"
```
_See [Test-FalconQuarantineAction](Test-FalconQuarantineAction)._

_2023-04-25: PSFalcon v2.2.5_
