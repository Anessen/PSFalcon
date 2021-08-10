## Positioning
Most PSFalcon commands have positional parameters, which means that you are able to omit the parameter name when running a command. However, this only works if you’re using the parameters in their proper sequence.

For instance, Invoke-FalconRTR works as expected in this example because `-Command` (position 1), `-Arguments` (position 2) and `-HostIds` (position 3) are all defined:
```powershell
Invoke-FalconRTR ls C:\Windows <id>, <id>
```
If `-Arguments` is _not_ included, this no longer works as PowerShell (or the API, depending on the context) thinks that `-HostIds` is supposed to be the value for `-Arguments`:
```powershell
Invoke-FalconRTR getsid <id>, <id>
```
## -All
The `-All` switch reads the pagination information in an API response and repeats requests to that API until all the available results are retrieved. Using this parameter allows you to ignore the `offset` and `after` fields and have PSFalcon handle the gathering of additional results.

## -Total
The `-Total` switch returns the total result count rather than the results themselves. It takes precedence over `-Detailed` and `-All`, so using either of those parameters with `-Total` will have no effect.

## -Detailed
If a PSFalcon command returns 'identifiers', you can use the `-Detailed` switch to pass the identifiers back to the command and retrieve more detailed information. For example, running `Get-FalconHost` will retrieve host identifiers, but using `Get-FalconHost -Detailed` is the same as running the two commands in this example:
```powershell
$Ids = Get-FalconHost
Get-FalconHost -Ids $ids
```
The `-Detailed` parameter will also break up the secondary command into appropriately sized groups, avoiding errors when retrieving details about large numbers of identifiers.
## Advanced Parameters
Each command was written as an [advanced function](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7) which enables support for common PowerShell parameters, including `-Verbose` which provides more explicit information during a request and help you understand how PSFalcon works.

_Learn more about [Commands](https://github.com/CrowdStrike/psfalcon/wiki/Commands)._