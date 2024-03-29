# Receive-FalconDiscoverAwsScript
## SYNOPSIS
Download a Bash script which grants Falcon Discover access using the AWS CLI
## DESCRIPTION
Requires 'AWS accounts: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Id|String[]|AWS Account identifier||||X|X|
|Force|Switch|Overwrite existing file when present||||||
## SYNTAX
```powershell
Receive-FalconDiscoverAwsScript [-Path] <String> [-Id] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-aws/entities/user-scripts-download/v1
```
### falconpy
[GetD4CAWSAccountScriptsAttachment](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#GetD4CAWSAccountScriptsAttachment)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
