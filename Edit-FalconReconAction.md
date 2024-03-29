# Edit-FalconReconAction
## SYNOPSIS
Modify a Falcon Intelligence Recon action
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Frequency|String|Action frequency|||`asap`<BR>`daily`<BR>`weekly`||X|
|Recipient|String[]|Email address|||||X|
|Status|String|Action status|||`enabled`<BR>`muted`||X|
|ContentFormat|String|Email format|||`standard`<BR>`enhanced`||X|
|TriggerMatchless|Boolean|Send email when no matches are found|||||X|
|Id|String|Action identifier|||||X|
## SYNTAX
```powershell
Edit-FalconReconAction [-Frequency] <String> [-Recipient] <String[]> [-Status] <String> [-ContentFormat] <String> [-TriggerMatchless] <Boolean> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /recon/entities/actions/v1
```
### falconpy
[UpdateActionV1](https://github.com/CrowdStrike/falconpy/wiki/recon#UpdateActionV1)
## USAGE
### Updating email notifications for a monitoring rule
```powershell
Edit-FalconReconAction -Id <id> -Frequency weekly
```

_2023-04-25: PSFalcon v2.2.5_
