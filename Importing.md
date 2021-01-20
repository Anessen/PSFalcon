## Importing into PowerShell

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