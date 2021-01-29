If not already present, install [PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
## Using the PowerShell Gallery
TO_DO
## Manual Installation
If you're unable to use the PowerShell Gallery to install the module, you can download directly from GitHub.

1. Download the [master repository](https://github.com/CrowdStrike/psfalcon/archive/master.zip) as a ZIP.
2. Unpack the archive and move the contents of the `psfalcon-master` folder into your User Modules directory:

**NOTE**: These commands assume you are running in a standard user (non-admin) PowerShell session and do not have [Folder Redirection](https://github.com/CrowdStrike/psfalcon/wiki/Installation#folder-redirection) enabled. Unpacking the module in the wrong place will lead to various errors that can prevent you from importing the module or running various commands (including malformed URLs).

* Linux/MacOS
```powershell
Expand-Archive ./psfalcon-master.zip .
Move-Item ./psfalcon-master/ $HOME/.local/share/powershell/Modules/PSFalcon/2.0.0
```
* Windows (PowerShell Core/6+)
```powershell
Expand-Archive .\psfalcon-master.zip .
Move-Item .\psfalcon-master\ $HOME\Documents\PowerShell\Modules\PSFalcon\2.0.0
```
* Windows (PowerShell Desktop/5.1)
```powershell
Expand-Archive .\psfalcon-master.zip .
Move-Item .\psfalcon-master\ $HOME\Documents\WindowsPowerShell\Modules\PSFalcon\2.0.0
```
If done correctly, your `PSFalcon\2.0.0` module folder will look like this:
```powershell
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           1/26/2021 10:40 AM                Class
d----           1/26/2021 10:40 AM                Data
d----           1/26/2021 10:40 AM                Private
d----           1/26/2021 10:40 AM                Public
-----           1/25/2021 10:37 AM           1946 LICENSE
-----           1/25/2021 10:37 AM          10838 PSFalcon.psd1
-----           1/25/2021 10:37 AM            944 PSFalcon.psm1
-----           1/25/2021 10:37 AM           1322 README.md
```
## Folder Redirection
If you have “Folder Redirection” in place, the `$HOME` folder may not be properly recognized by PowerShell. In these cases, you can extract PSFalcon and import the module directly:
```powershell
Expand-Archive .\psfalcon-master.zip .
Move-Item .\psfalcon-master\ .\PSFalcon
Import-Module .\PSFalcon
```
## Importing the Module
The PSFalcon module must be loaded at the beginning of a PowerShell session or script in order to access the commands included with PSFalcon.
### During a session
**NOTE**: The `Import-Module` command can be added to your PowerShell `$PROFILE` to automatically load the module when you start PowerShell.
```powershell
Import-Module -Name PSFalcon
```
### During the beginning of a script
```powershell
#Requires -Version 5.1 -Modules @{ModuleName='PSFalcon';ModuleVersion='2.0.0'}
```
_Learn more about [Commands](https://github.com/CrowdStrike/psfalcon/wiki/Commands)._
## Basic Troubleshooting
The `Start-Transcript` and `Stop-Transcript` PowerShell commands capture a PowerShell session to a log file, and using the `-Verbose` and `-Debug` parameters with each PSFalcon command will output additional information which can be useful in troubleshooting efforts.

If you run into any problems using PSFalcon, please capture a transcript of the commands you ran (including adding the `-Verbose` and `-Debug` parameters), and [create an issue on GitHub](https://github.com/CrowdStrike/psfalcon/issues).