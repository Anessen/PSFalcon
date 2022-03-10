![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
# Import the module
The PSFalcon module must be loaded at the beginning of a PowerShell session or script in order to access the commands included with PSFalcon.

## During a session
```powershell
Import-Module -Name PSFalcon
```
**NOTE**: The `Import-Module` command can be added to your PowerShell `$PROFILE` to automatically load the module when you start PowerShell.
## Within a script
```powershell
#Requires -Version 5.1
using module @{ ModuleName = 'PSFalcon'; ModuleVersion = '2.0' }
```
_Read more about [PowerShell profiles](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles)._

# List available commands
After importing the module you can view the list of commands provided with PSFalcon:
```powershell
Get-Command -Module PSFalcon
```

# Find help for a command
Information about PSFalcon commands and their parameters is available using the PowerShell `Get-Help` command.
```powershell
Get-Help Request-FalconToken
```
Using the `-Examples`, `-Detailed` or `-Full` parameter(s) provides additional information, but first requires that you `Update-Help`.
```powershell
Update-Help -Module PSFalcon
```

# Using parameters
Each PSFalcon command was written as an [advanced function](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_functions_advanced) which enables support for common PowerShell parameters.

Most PSFalcon commands have positional parameters, which means that you are able to omit the parameter name when running a command. However, this only works if you’re using the parameters in their proper sequence. For instance, `Invoke-FalconRtr` works as expected in this example because `-Command` (position 1), `-Arguments` (position 2) and `-HostIds` (position 3) are all defined.
```powershell
Invoke-FalconRtr ls C:\Windows <id>, <id>
```

If `-Arguments` is _not_ included, this no longer works as PowerShell (or the CrowdStrike API, depending on the context) thinks that `-HostIds` is supposed to be the value for `-Arguments`.
```powershell
Invoke-FalconRtr getsid <id>, <id>
```

## -All
By default, each PSFalcon command returns the first result from the API.

The `-All` switch reads the pagination information in an API response and repeats requests to that API until all the available results are retrieved. Using this parameter allows you to ignore the `Offset` and `After` parameters and have PSFalcon handle the gathering of additional results.

**NOTE**: Many CrowdStrike APIs are limited to a maximum of 10,000 results. `-All` will generate an error if it reaches this limit. Restricting your request using the `-Filter` parameter to ensure groups of less than 10,000 results will prevent this error from being generated.

## -Detailed
If a command returns identifier values for a specific resource, you can use the `-Detailed` switch to pass the identifiers back to the command and retrieve more detailed information. For example, running `Get-FalconHost` will retrieve host identifiers, but using `Get-FalconHost -Detailed` is the equivalent of running the two commands in this example.
```powershell
$Ids = Get-FalconHost
Get-FalconHost -Ids $Ids
```

The `-Detailed` parameter will create appropriately sized groups for the secondary command, avoiding limitations of the selected API when retrieving details about large numbers of identifiers.

## -Include
Some commands have an `-Include` parameter which pulls information from additional APIs and appends it to the final output. When this parameter is used, the appropriate permissions are required for the additional content to be added.

## -Total
The `-Total` switch returns the total result count rather than the results themselves. It takes precedence over `-Detailed` and `-All`, so using either of those parameters with `-Total` will have no effect.

# Converting output
The easiest way to export the results of a PSFalcon command and keep its structure intact is through conversion to Json.
```powershell
<command> [-Detailed] [-All] | ConvertTo-Json -Depth 16 | Out-File -FilePath .\example.json
```
If dealing with simple results, `Export-FalconReport` creates a modified `[PSCustomObject]` that will work within a CSV.
```powershell
<command> [-Detailed] [-All] | Export-FalconReport -Path .\example.csv
```
If you wish to validate the output before creating a CSV, use `Export-FalconReport` without a `-Path` value:
```powershell
<command> [-Detailed] [-All] | Export-FalconReport
```

**WARNING**: Because the results are manipulated by `Export-FalconReport` and PowerShell can modify the CSV output depending on the content included within the first object, some data may be lost. Converting to Json ensures the highest accuracy of the output.