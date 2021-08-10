# Use the PowerShell Gallery
The PowerShell Gallery offers the easiest method to install PSFalcon. If not already present, you must install [PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) before proceeding.
## Verify your Execution Policy
The module included on the PowerShell Gallery is signed and requires an ExecutionPolicy of `RemoteSigned` or lower (Bypass and Unrestricted will also work, though they are less secure). If your ExecutionPolicy is set to `Restricted` you will not be able to install the module from the PowerShell Gallery. You can check your current ExecutionPolicy with `Get-ExecutionPolicy` and change it to `RemoteSigned` using `Set-ExecutionPolicy`.
```powershell
Get-ExecutionPolicy
```
## Download the module
Use the `Install-Module` command to download and install the module under your user account.
```powershell
Install-Module -Name PSFalcon -Scope CurrentUser
```
You may be prompted with a warning that the PowerShell Gallery is an untrusted repository. You can accept and continue to install the module. You can permanently change this using `Set-PSRepository`. You may also be prompted to update your NuGet package to interact with the PowerShell Gallery. This is the method that the gallery uses to install modules and is required to use it.

If you're running an older version of PSFalcon, you must include the `-Force` parameter to verify that you'd like to install the latest version alongside the old version. You can use `Uninstall-Module -Name PSFalcon -AllVersions` to remove all existing versions of the module.
If the PowerShell Gallery isn't accessible in your environment or the installation failed, you can try a [Manual Installation](https://github.com/CrowdStrike/psfalcon/wiki/Installation#manual-installation).
# Import the Module
The PSFalcon module must be loaded at the beginning of a PowerShell session or script in order to access the commands included with PSFalcon.
## During a session
**NOTE**: The `Import-Module` command can be added to your PowerShell `$PROFILE` to automatically load the module when you start PowerShell.
```powershell
Import-Module -Name PSFalcon
```
## During the beginning of a script
```powershell
#Requires -Version 5.1 -Modules @{ModuleName='PSFalcon';ModuleVersion='<version>'}
```
_Learn more about [Commands](https://github.com/CrowdStrike/psfalcon/wiki/Commands)._
# Basic Troubleshooting and Support
* Set `$VerbosePreference` and `$DebugPreference` to `'Continue'`
* Run `Start-Transcript`, `Show-FalconModule`, the affected PSFalcon commands or script, and `Stop-Transcript`
* [Create an issue on GitHub](https://github.com/CrowdStrike/psfalcon/issues)
## Folder Redirection
If you have “Folder Redirection” in place, the `$HOME` folder may not be properly recognized by PowerShell. In these
cases, you can [extract PSFalcon](https://github.com/CrowdStrike/psfalcon/wiki/Installation#manual-installation) and import the module directly:
```powershell
Expand-Archive .\psfalcon-<version>.zip .
Move-Item .\psfalcon-<version>\ .\PSFalcon
Import-Module .\PSFalcon
```
# Manual Installation
If you're unable to use the PowerShell Gallery to install the module, you can download directly from GitHub. **_If the installation from the PowerShell Gallery worked, there's no need to follow any of the steps included in this section._**

1. Download the [latest release](https://github.com/CrowdStrike/psfalcon/releases) as a ZIP
2. Unpack the archive and move the contents of the folder into your User Modules directory

**NOTE**: These commands assume you are running in a standard user (non-admin) PowerShell session and do not have [Folder Redirection](https://github.com/CrowdStrike/psfalcon/wiki/Installation#folder-redirection) enabled. Unpacking the module in the wrong place will lead to various errors that can prevent you from importing the module or running various commands.

**NOTE**: You may receive an error about the destination folders not existing when attempting to move the module files. If you do, create the folders first then move the module files into them.

*Read more about [Installing PowerShell Modules](https://docs.microsoft.com/en-us/powershell/scripting/developer/module/installing-a-powershell-module)*.
* Linux/MacOS
```powershell
Expand-Archive ./psfalcon-<version>.zip .
Move-Item ./psfalcon-<version>/ $HOME/.local/share/powershell/Modules/PSFalcon/<version>/ -Force
```
* Windows (PowerShell Core/6+)
```powershell
Expand-Archive .\psfalcon-<version>.zip .
Move-Item .\psfalcon-<version>\ $HOME\Documents\PowerShell\Modules\PSFalcon\<version>\ -Force
```
* Windows (PowerShell Desktop/5.1)
```powershell
Expand-Archive .\psfalcon-<version>.zip .
Move-Item .\psfalcon-<version>\ $HOME\Documents\WindowsPowerShell\Modules\PSFalcon\<version>\ -Force
```
If done correctly, your `PSFalcon\<version>` module folder will look like this:
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