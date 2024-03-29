# New-FalconReconAction
## SYNOPSIS
Create Falcon Intelligence Recon monitoring rule actions
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|RuleId|String|Monitoring rule identifier|||||X|
|Type|String|Notification type|||`email`||X|
|Frequency|String|Notification frequency|||`asap`<BR>`daily`<BR>`weekly`||X|
|Recipient|String[]|Notification recipient|||||X|
|ContentFormat|String|Email format|||`standard`<BR>`enhanced`||X|
|TriggerMatchless|Boolean|Send email when no matches are found|||||X|
## SYNTAX
```powershell
New-FalconReconAction [-RuleId] <String> [-Type] <String> [-Frequency] <String> [-Recipient] <String[]> [[-ContentFormat] <String>] [[-TriggerMatchless] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /recon/entities/actions/v1
```
### falconpy
[CreateActionsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#CreateActionsV1)
## USAGE
### Creating email notifications for a monitoring rule
```powershell
New-FalconReconAction -RuleId <rule_id> -Type email -Frequency daily -Recipients user@example.com
```

_2023-04-25: PSFalcon v2.2.5_
