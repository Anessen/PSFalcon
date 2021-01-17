# Command List

After importing the module you can view the list of commands provided with PSFalcon:

```powershell
Get-Command -Module PSFalcon
```

# Command-based Help

Because PSFalcon uses dynamic parameters, the traditional PowerShell `Get-Help` command doesn't show parameters that can be used with PSFalcon commands. Instead, use `<command> -Help` to call a custom function that displays information about the available parameters and a basic description of their use.

### _See Also_
[Parameters](https://github.com/CrowdStrike/psfalcon/wiki/Parameters)