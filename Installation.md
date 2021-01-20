If not already present, install [PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
## Using the PowerShell Gallery
TO_DO
## Manual Installation
If you're unable to use the PowerShell Gallery to install the module, you can download directly from GitHub.

1. Download the [master repository](https://github.com/CrowdStrike/psfalcon/archive/master.zip) as a ZIP.
2. Unpack the archive and move the contents of the `psfalcon-master` folder into your User Modules directory:

* Linux/MacOS
```powershell
$HOME/.local/share/powershell/Modules/PSFalcon/2.0.0
```
* Windows (PowerShell Core/6+)
```powershell
$HOME\Documents\PowerShell\Modules\PSFalcon\2.0.0
```
* Windows (PowerShell Desktop/5.1)
```powershell
$HOME\Documents\WindowsPowerShell\Modules\PSFalcon\2.0.0
```
## Folder Redirection
If you have “Folder Redirection” in place, the `$HOME` folder may not be properly recognized by PowerShell. In these cases, you can extract PSFalcon to a different folder and import the module directly from that folder when you want to use it.

For instance, if you unpacked it in a folder called "PSFalcon", you could navigate to the directory that folder is contained in and point `Import-Module` to the directory:
```powershell
Import-Module .\PSFalcon
```
## Importing the Module
Once installed, PSFalcon needs to be [imported into PowerShell](https://github.com/CrowdStrike/psfalcon/wiki/Importing) whenever you wish to use the included commands.