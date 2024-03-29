# Add-FalconCompleteActivity
## SYNOPSIS
Add an activity to a Falcon Complete case
## DESCRIPTION
Requires 'Message Center: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Type|String|Activity type|||`comment`|||
|Content|String|Activity content||||||
|UserId|String|User identifier|||||X|
|Id|String|Case identifier|||||X|
## SYNTAX
```powershell
Add-FalconCompleteActivity [-Type] <String> [-Content] <String> [-UserId] <String> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /message-center/entities/case-activity/v1
```
### falconpy
[CaseAddActivity](https://github.com/CrowdStrike/falconpy/wiki/message-center#CaseAddActivity)
## USAGE
## Adding a message to an existing case
```powershell
Add-FalconCompleteActivity -Id <id> -UserId <user_uuid> -Type 'comment' -Content 'Is this still an issue in my environment?'
```
_See [Find a user ID by username](Users-and-Roles#find-a-user-id-by-username)_.

_2023-04-25: PSFalcon v2.2.5_
