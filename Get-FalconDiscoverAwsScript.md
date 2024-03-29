# Get-FalconDiscoverAwsScript
## SYNOPSIS
Generate a bulk registration script for Falcon Discover
## DESCRIPTION
Requires 'AWS accounts: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|OrganizationId|String|AWS organization identifier|||||X|
|AccountType|String|Account type, when registering AWS commercial account in a Gov environment|||`commercial`<BR>`gov`||X|
|SingleAccount|Boolean|Provide static script for a single AWS account||||||
|Delete|Boolean|Generate a delete script||||||
## SYNTAX
```powershell
Get-FalconDiscoverAwsScript [[-OrganizationId] <String>] [[-AccountType] <String>] [[-SingleAccount] <Boolean>] [[-Delete] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /settings-discover/entities/gen/scripts/v1
```
### falconpy
[GetHorizonD4CScripts](https://github.com/CrowdStrike/falconpy/wiki/settings-discover#GetHorizonD4CScripts)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
