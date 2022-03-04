![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
# Installation
## Use the PowerShell Gallery
The PowerShell Gallery is the recommended way to install the module. If not present, you must [install PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) before proceeding.

### Verify your execution policy (Optional)
The module included on the PowerShell Gallery is signed and requires an ExecutionPolicy of `RemoteSigned` or lower. If your ExecutionPolicy is set to `Restricted` you will not be able to install the module from the PowerShell Gallery. You can check your current ExecutionPolicy with `Get-ExecutionPolicy` and change it to `RemoteSigned` using `Set-ExecutionPolicy`.

```powershell
Get-ExecutionPolicy
```

### Download the module
Use the `Install-Module` command to download and install the module under your user account.

```powershell
Install-Module -Name PSFalcon -Scope CurrentUser
```

You may be prompted with a warning that the PowerShell Gallery is an untrusted repository. You can accept and continue to install the module. You can permanently change this using `Set-PSRepository`. You may also be prompted to update your NuGet package to interact with the PowerShell Gallery. This is the method that the gallery uses to install modules and is required to use it.

If you're running an older version of PSFalcon, you must include the `-Force` parameter to verify that you'd like to install the latest version alongside the old version. You can use `Uninstall-Module -Name PSFalcon -AllVersions` to remove all existing versions of the module.

If the PowerShell Gallery isn't accessible in your environment or the installation failed you can install using a GitHub release.

## Download from GitHub
Installing using a GitHub release is only recommended if the PowerShell Gallery is not available within your environment. **_If the installation from the PowerShell Gallery worked, there's no need to follow any of the steps included in this section._**

1. Download the [latest release](https://github.com/CrowdStrike/psfalcon/releases)
2. Unpack the archive and move the contents of the folder into your User Modules directory

_See [Installing PowerShell Modules](https://docs.microsoft.com/en-us/powershell/scripting/developer/module/installing-a-powershell-module)._

### Expand archive and move to the proper module folder
**NOTE**: You may receive an error about the destination folders not existing when attempting to move the module files. If you do, create the folders first then move the module files into them.

**Linux/MacOS**
```powershell
Expand-Archive ./psfalcon-<version>.zip .
Move-Item ./psfalcon-<version>/ $HOME/.local/share/powershell/Modules/PSFalcon/<version>/ -Force
```

**Windows \(PowerShell Core/6+\)**
```powershell
Expand-Archive .\psfalcon-<version>.zip .
Move-Item .\psfalcon-<version>\ $HOME\Documents\PowerShell\Modules\PSFalcon\<version>\ -Force
```

**Windows \(PowerShell Desktop/5.1\)**
```powershell
Expand-Archive .\psfalcon-<version>.zip .
Move-Item .\psfalcon-<version>\ $HOME\Documents\WindowsPowerShell\Modules\PSFalcon\<version>\ -Force
```

If done correctly, your `PSFalcon\<version>` folder will look similar to the following example.

```powershell
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           1/26/2021 10:40 AM                Class
d----           1/26/2021 10:40 AM                Private
d----           1/26/2021 10:40 AM                Public
-----           1/25/2021 10:37 AM           1946 LICENSE
-----           1/25/2021 10:37 AM          10838 PSFalcon.psd1
-----           1/25/2021 10:37 AM            944 PSFalcon.psm1
-----           1/25/2021 10:37 AM           1322 README.md
```

### Use another folder
If you have folder redirection in place, the `$HOME` folder may not be properly recognized by PowerShell. In these
cases, you can extract PSFalcon and import the module directly.

```powershell
Expand-Archive .\psfalcon-<version>.zip .
Move-Item .\psfalcon-<version>\ .\PSFalcon
```

# Upgrade
If the PowerShell Gallery was used to install the module, it can also be used to upgrade.
```powershell
Update-Module -Name PSFalcon
```

**NOTE**: If the update fails, remove all existing versions of PSFalcon and install the new version.

If the module was manually installed, delete your existing PSFalcon module folder and install the new version.

# Removal
If the PSFalcon module folder exists within the proper module path, you can use `Uninstall-Module` to remove it. Including the optional `-AllVersions` parameter will ensure that all instances of PSFalcon are removed.
```powershell
Uninstall-Module -Name PSFalcon -AllVersions
```
If PSFalcon was manually installed, simply delete the module folder.