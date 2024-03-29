# Test-FalconFirewallPath
## SYNOPSIS
Validate that a string matches a Firewall Management executable filepath glob pattern
## DESCRIPTION
Requires 'Firewall management: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Pattern|String|Glob pattern||||||
|String|String|Filepath string||||||
## SYNTAX
```powershell
Test-FalconFirewallPath [-Pattern] <String> [-String] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /fwmgr/entities/rules/validate-filepath/v1
```
### falconpy
[validate_filepath_pattern](https://github.com/CrowdStrike/falconpy/wiki/firewall-management#validate_filepath_pattern)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
