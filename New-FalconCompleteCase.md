# New-FalconCompleteCase
## SYNOPSIS
Create a Falcon Complete case
## DESCRIPTION
Requires 'Message Center: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Type|String|Case type|||`fc:detection-support`<BR>`fc:contact`<BR>`fc:falcon-product-support`<BR>`fc:incident-support`|||
|Title|String|Case title||||||
|Content|String|Case content||||||
|DetectionId|String[]|Detection identifier|||||X|
|IncidentId|String[]|Incident identifier|||||X|
|UserId|String|User identifier|||||X|
## SYNTAX
```powershell
New-FalconCompleteCase [-Type] <String> [-Title] <String> [-Content] <String> [[-DetectionId] <String[]>] [[-IncidentId] <String[]>] [-UserId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /message-center/entities/case/v2
```
### falconpy
[CreateCaseV2](https://github.com/CrowdStrike/falconpy/wiki/message-center#CreateCaseV2)
## USAGE
### Getting support for a detection
```powershell
New-FalconCompleteCase -UserId <user_uuid> -Type 'fc:detection-support' -Title 'support case with detection' -Content 'case with detection' -DetectionId <id>, <id>
```
_See [Find detections](Incident-and-Detection-Monitoring#find-detections)_.
### Getting support for an incident
```powershell
New-FalconCompleteCase -UserId <user_uuid> -Type 'fc:incident-support' -Title 'support case with incident' -Content 'case with incident' -IncidentId <id>, <id>
```
_See [Find incidents](Incident-and-Detection-Monitoring#find-incidents)_.
### Contacting the Falcon Complete team
```powershell
New-FalconCompleteCase -UserId <user_uuid> -Type 'fc:contact' -Title 'falcon complete support case' -Content 'falcon complete support case'
```
_See [Find a user ID by username](Users-and-Roles#find-a-user-id-by-username)_.
### Getting general support for Falcon products
```powershell
New-FalconCompleteCase -UserId <user_uuid> -Type 'fc:falcon-product-support' -Title 'contact support' -Content 'contact support'
```
_See [Find a user ID by username](Users-and-Roles#find-a-user-id-by-username)_.

_2023-04-25: PSFalcon v2.2.5_
