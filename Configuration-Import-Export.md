![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
***
- [Export all configurations](#export-all-configurations)
    - [Export specific configurations](#export-specific-configurations)
- [Import configurations](#import-configurations)
    - [AssignExisting](#assignexisting)
    - [ModifyExisting](#modifyexisting)
    - [ModifyDefault](#modifydefault)
***
|Command|Permission|
|-------|----------|
|[Export-FalconConfig](#export-all-configurations)||
|[Import-FalconConfig](#import-configurations)||
***
# Export all configurations
The `Export-FalconConfig` command gathers configurable items from your Falcon environment and exports them as a
ZIP archive. The following example will create a file called `FalconConfig_<FileDateTime>.zip` in your current
directory containing all the available configurations.
```powershell
Export-FalconConfig
```
**NOTE**: Users are not included in the export/import process because they are unique and cannot be duplicated.
## Export specific configurations
Similar to the regular command, a zip file will be created, but in this example it will only include `HostGroup`,
`FirewallGroup` (including Firewall Rules) and `FirewallPolicy` items.
```powershell
Export-FalconConfig -Select HostGroup, FirewallGroup, FirewallPolicy
```
# Import configurations
Using the `Import-FalconConfig` command, you can re-create any items that are present in the export but are not
present in your authenticated Falcon environment. `Import-FalconConfig` loads the files within the ZIP, checks
them against the existing items in the target environment, and creates any items that are not present.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip
```
**NOTE**: Unless `AssignExisting` is included, items that depend on the existence of a specific host group will
not be created.

For example, if you attempt to import a Machine Learning Exclusion that is assigned to the host group "Example
Group" and "Example Group" already exists in your environment, the exclusion will not be created. If it is
possible to create the item without the dependency \(like a policy without assigned host groups\), it
will be created.

## AssignExisting
Including the `AssignExisting` parameter when running `Import-FalconConfig` will cause existing host groups to
be assigned to created items when they match groups that would have been created as part of the import.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip -AssignExisting
```
If `AssignExisting` is not specified, existing items will not be assigned to created items when using
`Import-FalconConfig`.
## ModifyExisting
The `ModifyExisting` parameter forces the `Import-FalconConfig` command to analyze and modify a list of selected
items based on your target import.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip -ModifyExisting PreventionPolicy, SensorUpdatePolicy
```
If `ModifyExisting` is not specified, existing items will not be modified when using `Import-FalconConfig`.
## ModifyDefault
`ModifyDefault` works similarly to `ModifyExisting`, but allows `Import-FalconConfig` to modify
`platform_default` policies based on your target import.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDateTime>.zip -ModifyDefault PreventionPolicy
```
If `ModifyDefault` is not specified, `platform_default` policies will not be modified when using
`Import-FalconConfig`.