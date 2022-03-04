![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)

The `Export-FalconConfig` command gathers configurable items from your Falcon environment and exports them as json files in a zip archive. Using the `Import-FalconConfig` command, you can re-create any items that are present in the export but are not present in your authenticated Falcon environment. 

The `Export-FalconConfig` and `Import-FalconConfig` commands require read and write permissions for all of the associated item types (Host Groups, Policies, Exclusions, etc.).

**NOTE**: Only non-existing items will be imported. No existing policies, groups, exclusions or rules will be modified.

**NOTE**: If you attempt to import an item that depends on another item and that dependency was not created, then the item itself will not be created either. For example, if you attempt to import a Machine Learning Exclusion that is assigned to the Host Group "Example Group" and "Example Group" already exists in your environment, the exclusion will not be created. However, if it is possible to create the item without the dependency (like a policy without assigned Host Groups), it will still be created.

# Export all configurations
This will create a file called `FalconConfig_<FileDate>.zip` in your current directory containing all the available configuration options.
```powershell
Export-FalconConfig
```
## Export specific configurations
Similar to the regular command, a zip file will be created, but in this example it will only include `HostGroup`, `FirewallGroup` (including Firewall Rules) and `FirewallPolicy` items.
```powershell
Export-FalconConfig -Items HostGroup, FirewallGroup, FirewallPolicy
```
# Import configurations
When you run the `Import-FalconConfig` command, all of the files within the zip will be loaded and the corresponding items will be retrieved from your authenticated Falcon environment for analysis. If one or more of the items aren't present in your environment, they will be created.
```powershell
Import-FalconConfig -Path .\FalconConfig_<FileDate>.zip
```