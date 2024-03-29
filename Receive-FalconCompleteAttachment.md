# Receive-FalconCompleteAttachment
## SYNOPSIS
Download a Falcon Complete case attachment
## DESCRIPTION
Requires 'Message Center: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Id|String|Attachment identifier||||X|X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconCompleteAttachment [-Path] <String> [-Id] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /message-center/entities/case-attachment/v1
```
### falconpy
[CaseDownloadAttachment](https://github.com/CrowdStrike/falconpy/wiki/message-center#CaseDownloadAttachment)
## USAGE
### Download a file attachment from a case
```powershell
Receive-FalconCompleteAttachment -Id <id> -Path .\test.jpg
```

_2023-04-25: PSFalcon v2.2.5_
