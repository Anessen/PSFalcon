# Get-FalconDeviceControlPolicy
## SYNOPSIS
Search for Falcon Device Control policies
## DESCRIPTION
Requires 'Device control policies: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Policy identifier||||X|X|
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results<BR><BR>`created_by`<BR>`created_timestamp`<BR>`description`<BR>`enabled`<BR>`groups`<BR>`modified_by`<BR>`modified_timestamp`<BR>`name`<BR>`name.raw`<BR>`platform_name`||||||
|Sort|String|Property and direction to sort results|||`created_by.asc`<BR>`created_by.desc`<BR>`created_timestamp.asc`<BR>`created_timestamp.desc`<BR>`enabled.asc`<BR>`enabled.desc`<BR>`modified_by.asc`<BR>`modified_by.desc`<BR>`modified_timestamp.asc`<BR>`modified_timestamp.desc`<BR>`name.asc`<BR>`name.desc`<BR>`platform_name.asc`<BR>`platform_name.desc`<BR>`precedence.asc`<BR>`precedence.desc`|||
|Limit|Int32|Maximum number of results per request|`1`|`5000`||||
|Include|String[]|Include additional properties|||`members`|||
|Offset|Int32|Position to begin retrieving results||||||
|Default|Switch|Retrieve default Device Control policy, including notification content||||||
|Detailed|Switch|Retrieve detailed information||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconDeviceControlPolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconDeviceControlPolicy -Id <String[]> [[-Include] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconDeviceControlPolicy [[-Filter] <String>] [[-Sort] <String>] [[-Limit] <Int32>] [[-Include] <String[]>] [-Offset <Int32>] -Detailed [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Get-FalconDeviceControlPolicy -Default [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /policy/combined/device-control/v1
GET /policy/entities/default-device-control/v1
GET /policy/entities/device-control/v1
GET /policy/queries/device-control/v1
```
### falconpy
[queryDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#queryDeviceControlPolicies)<BR>[getDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#getDeviceControlPolicies)<BR>[queryCombinedDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#queryCombinedDeviceControlPolicies)<BR>[getDefaultDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#getDefaultDeviceControlPolicies)
## USAGE
### Find policy details using a filtered search
```powershell
Get-FalconDeviceControlPolicy -Filter "name:'policy'" -Sort created_timestamp.asc -Detailed
```
### List policy ids using a filtered search
```powershell
Get-FalconDeviceControlPolicy -Filter "name:'diana.hudson'" -Sort name.desc -Detailed
```
### List details about specific policies
```powershell
Get-FalconDeviceControlPolicy -Id <id>, <id>
```
### Export a list of policy members including the most recent interactive user
**NOTE**: The example uses a `name` filter to target a policy named `my_policy`.
```powershell
foreach ($Policy in (Get-FalconDeviceControlPolicy -Filter "name:'my_policy'" -Include members -Detailed)) {
    foreach ($Device in (Get-FalconHost -Id $Policy.members.device_id -Login)) {
        foreach ($Member in @($Policy.members).Where({ $_.device_id -eq $Device.device_id })) {
            $Recent = @($Device.recent_logins).Where({ $_.user_name -match $Member.hostname }) | Select-Object -First 1
            [PSCustomObject]@{
                policy_id = $Policy.id
                policy_name = $Policy.name
                device_id = $Member.device_id
                hostname = $Member.hostname
                most_recent_user_name = $Recent.user_name
                most_recent_login_time = $Recent.login_time
            } | Export-Csv .\policy_members.csv -NoTypeInformation -Append
        }
    }
}
```

_2023-04-25: PSFalcon v2.2.5_
