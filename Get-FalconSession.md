# Get-FalconSession
## SYNOPSIS
Search for Real-time Response sessions
## DESCRIPTION
Real-time Response sessions are segmented by permission, meaning that only sessions that were created using
your OAuth2 API Client will be visible. Use the 'Cid' switch to enable viewing of sessions from your entire
environment.

'Get-FalconQueue' can be used to find and export information about sessions in the 'offline queue'.

Requires 'Real time response: Read', and 'Real time response audit: Read' when using the 'Cid' switch.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Session identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results||||||
|Limit|Int32|Maximum number of results per request|`1`|`1000`||||
|CommandInfo|Boolean|||||||
|Offset|Int32|Position to begin retrieving results||||||
|Cid|Switch|Expand search to include all sessions created within your environment||||||
|Queue|Switch|Restrict search to sessions that have been queued||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconSession [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [-Offset <Int32>] [-Detailed] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSession -Id <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSession -Id <String[]> -Queue [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconSession [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-CommandInfo] <Boolean>] [-Offset <Int32>] -Cid [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /real-time-response/queries/sessions/v1
GET /real-time-response-audit/combined/sessions/v1
POST /real-time-response/entities/queued-sessions/GET/v1
POST /real-time-response/entities/sessions/GET/v1
```
### falconpy
[RTR_ListAllSessions](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListAllSessions)<BR>[RTR_ListSessions](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListSessions)<BR>[RTR_ListQueuedSessions](https://github.com/CrowdStrike/falconpy/wiki/real-time-response#RTR_ListQueuedSessions)<BR>[RTRAuditSessions](https://github.com/CrowdStrike/falconpy/wiki/real-time-response-audit#RTRAuditSessions)
## USAGE
### List sessions
**NOTE**: Only sessions created by your OAuth2 API Client will be visible using the following commands.
```powershell
Get-FalconSession [-Detailed] [-All]
```
### Retrieve detail about sessions
**NOTE**: Only sessions created by your OAuth2 API Client will be visible using the following commands.
```powershell
Get-FalconSession -Id <id>, <id>
```
Use the `Queue` switch when the session has been queued for offline host(s):
```powershell
Get-FalconSession -Id <id>, <id> -Queue
```

_2023-11-27: PSFalcon v2.2.6_
