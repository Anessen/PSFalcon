## Install PowerShell

If not already present, install [PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).

## Use the PowerShell Gallery
TODO

## Manual Installation using GitHub

1. Download the [master repository](https://github.com/CrowdStrike/psfalcon/archive/master.zip) as a ZIP.
2. Unpack the archive and move the contents of the "psfalcon-master" folder into your User Modules directory:
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

**NOTE**: If you have “Folder Redirection” in place via Group Policy, the `$HOME` folder may not be properly recognized by PowerShell. In these cases, you can extract PSFalcon to a different folder and import the module directly from that folder when you want to use it. For instance, if you unpacked it in a folder called "PSFalcon", you could navigate to the directory that folder is contained in and point `Import-Module` to the directory:

```powershell
Import-Module .\PSFalcon
```

## Importing the PSFalcon Module
The PSFalcon module must be loaded at the beginning of a PowerShell session or script in order to access the commands included with PSFalcon.

### PowerShell Session

**NOTE**: The `Import-Module` command can be added to your PowerShell `$PROFILE` to automatically load the module when you start PowerShell.

```powershell
Import-Module -Name PSFalcon
```

### PowerShell Script

```powershell
#Requires -Version 5.1 -Modules @{ModuleName='PSFalcon';ModuleVersion='2.0.0'}
```