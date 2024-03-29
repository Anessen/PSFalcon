# Import-FalconConfig
## SYNOPSIS
Import items from a 'FalconConfig' archive into your Falcon environment
## DESCRIPTION
Creates groups, policies, exclusions, rules and scripts within a 'FalconConfig' archive within your authenticated
Falcon environment.

Anything that already exists will be ignored and no existing items will be modified unless the relevant switch
parameters are included.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|FalconConfig archive path||||||
|AssignExisting|Switch|Assign existing host groups with identical names to imported items||||||
|ModifyDefault|String[]|Modify specified 'platform_default' policies to match import|||`DeviceControlPolicy`<BR>`FirewallPolicy`<BR>`PreventionPolicy`<BR>`ResponsePolicy`<BR>`SensorUpdatePolicy`|||
|ModifyExisting|String[]|Modify existing specified items to match import|||`DeviceControlPolicy`<BR>`FileVantagePolicy`<BR>`FileVantageRuleGroup`<BR>`FirewallGroup`<BR>`FirewallPolicy`<BR>`HostGroup`<BR>`IoaExclusion`<BR>`IoaGroup`<BR>`Ioc`<BR>`MlExclusion`<BR>`PreventionPolicy`<BR>`ResponsePolicy`<BR>`Script`<BR>`SensorUpdatePolicy`<BR>`SvExclusion`|||
## SYNTAX
```powershell
Import-FalconConfig [-Path] <String> [-AssignExisting] [-ModifyDefault <String[]>] [-ModifyExisting <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Import configurations
Using the `Import-FalconConfig` command, you can re-create any items that are present in the export but are not
present in your authenticated Falcon environment. `Import-FalconConfig` loads the files within the ZIP, checks
them against the existing items in the target environment, and creates any items that are not present.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip
```
**NOTE**: Unless `AssignExisting` is included, items that depend on the existence of a specific host group will
not be created.  For example, if you attempt to import a Machine Learning Exclusion that is assigned to the host
group "Example Group" and "Example Group" already exists in your environment, the exclusion will not be created.

If it is possible to create the item without the dependency \(like a policy without assigned host groups\), it
will be created. 
### AssignExisting
Including the `AssignExisting` parameter when running `Import-FalconConfig` will cause existing host groups to be
assigned to created items when they match groups that would have been created as part of the import.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip -AssignExisting
```
If `AssignExisting` is not specified, existing items will not be assigned to created items when using
`Import-FalconConfig`.
### ModifyExisting
The `ModifyExisting` parameter forces the `Import-FalconConfig` command to analyze and modify a list of selected
items based on your target import.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip -ModifyExisting PreventionPolicy, SensorUpdatePolicy
```
If `ModifyExisting` is not specified, existing items will not be modified when using `Import-FalconConfig`.
### ModifyDefault
`ModifyDefault` works similarly to `ModifyExisting`, but allows `Import-FalconConfig` to modify
`platform_default` policies based on your target import.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip -ModifyDefault PreventionPolicy
```
If `ModifyDefault` is not specified, `platform_default` policies will not be modified when using
`Import-FalconConfig`.

_See [Export-FalconConfig](Export-FalconConfig)_.

_2023-11-27: PSFalcon v2.2.6_
