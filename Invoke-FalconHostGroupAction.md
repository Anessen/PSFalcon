# Invoke-FalconHostGroupAction
## SYNOPSIS
Perform actions on host groups
## DESCRIPTION
Adds or removes hosts from host groups in batches of 500.

Requires 'Host groups: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`add-hosts`<BR>`remove-hosts`|||
|Id|String|Host group identifier||||||
|HostId|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconHostGroupAction [-Name] <String> [-Id] <String> [-HostId] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /devices/entities/host-group-actions/v1
```
### falconpy
[performGroupAction](https://github.com/CrowdStrike/falconpy/wiki/host-group#performGroupAction)
## USAGE
### Managing hosts in a static host group
```powershell
Invoke-FalconHostGroupAction -Name add-hosts -Id <id> -HostId <id>, <id>
```
```powershell
Invoke-FalconHostGroupAction -Name remove-hosts -Id <id> -HostId <id>, <id>
```
_See [Add a list of hostnames to a host group](https://github.com/CrowdStrike/psfalcon/blob/master/samples/host_groups/add-a-list-of-hostnames-to-a-host-group.ps1)._

_2023-04-25: PSFalcon v2.2.5_
