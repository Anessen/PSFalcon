![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)

## Export all configurations
The `Export-FalconConfig` command gathers configurable items from your Falcon environment and exports them as a
ZIP archive. The following example will create a file called `FalconConfig_<FileDate>.zip` in your current
directory containing all the available configurations.
```powershell
Export-FalconConfig
```
**NOTE**: Users are not included in the export/import process because they are unique and can not be duplicated.
### Export specific configurations
Similar to the regular command, a zip file will be created, but in this example it will only include `HostGroup`,
`FirewallGroup` (including Firewall Rules) and `FirewallPolicy` items.
```powershell
Export-FalconConfig -Items HostGroup, FirewallGroup, FirewallPolicy
```
## Import configurations
Using the `Import-FalconConfig` command, you can re-create any items that are present in the export but are not
present in your authenticated Falcon environment. `Import-FalconConfig` loads the files within the ZIP, checks
them against the existing items in the target environment, and creates any items that are not present.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDate>.zip
```
**NOTE**: If you attempt to import an item that depends on another item and that dependency was not created, then
the item itself will not be created.

For example, if you attempt to import a Machine Learning Exclusion that is assigned to the Host Group "Example
Group" and "Example Group" already exists in your environment, the exclusion will not be created. Including the
`-Force` parameter when running `Import-FalconConfig` will cause existing Host Groups to be used when they match
groups that would have been created as part of the import.

If it is possible to create the item without the dependency \(like a policy without assigned Host Groups\), it
will still be created.

**WARNING**: Only non-existing items will be imported. No existing policies, groups, exclusions or rules will be
modified.