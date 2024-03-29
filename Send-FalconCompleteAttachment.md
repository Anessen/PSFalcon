# Send-FalconCompleteAttachment
## SYNOPSIS
Upload and attach a file to a Falcon Complete case
## DESCRIPTION
Requires 'Message Center: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Path to local file||||||
|UserId|String|User identifier|||||X|
|Id|String|Case identifier|||||X|
## SYNTAX
```powershell
Send-FalconCompleteAttachment [-Path] <String> [-UserId] <String> [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /message-center/entities/case-attachment/v1
```
### falconpy
[CaseAddAttachment](https://github.com/CrowdStrike/falconpy/wiki/message-center#CaseAddAttachment)
## USAGE
### Upload a file attachment to a case
```powershell
Send-FalconCompleteAttachment -Id <id> -Path C:\Users\jdoe\testdata\test.jpg
```

_2023-04-25: PSFalcon v2.2.5_
