# Export-FalconConfig
## SYNOPSIS
Create an archive containing Falcon configuration files
## DESCRIPTION
Uses various PSFalcon commands to gather and export groups, policies and exclusions as a collection of Json files
within a zip archive. The exported files can be used with 'Import-FalconConfig' to restore configurations to your
existing CID or create them in another CID.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Select|String[]|Selected items to export from your current CID, or leave unspecified to export all available items|||`DeviceControlPolicy`<BR>`FileVantagePolicy`<BR>`FileVantageRuleGroup`<BR>`FirewallGroup`<BR>`FirewallPolicy`<BR>`HostGroup`<BR>`IoaExclusion`<BR>`IoaGroup`<BR>`Ioc`<BR>`MlExclusion`<BR>`PreventionPolicy`<BR>`ResponsePolicy`<BR>`Script`<BR>`SensorUpdatePolicy`<BR>`SvExclusion`|||
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Export-FalconConfig [[-Select] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Export all configurations
The `Export-FalconConfig` command gathers configurable items from your Falcon environment and exports them as a
ZIP archive. The following example will create a file called `FalconConfig_<FileDateTime>.zip` in your current
directory containing all the available configurations.
```powershell
Export-FalconConfig
```
**NOTE**: Users are not included in the export/import process because they are unique and cannot be duplicated.
### Export specific configurations
Similar to the regular command, a zip file will be created, but in this example it will only include `HostGroup`,
`FirewallGroup` (including Firewall Rules) and `FirewallPolicy` items.
```powershell
Export-FalconConfig -Select HostGroup, FirewallGroup, FirewallPolicy
```

_See [Import-FalconConfig](Import-FalconConfig)_.

_2023-11-27: PSFalcon v2.2.6_
