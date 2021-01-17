# Positioning

Most PSFalcon commands have positional parameters (listed when using `-Help`), which means that you are able to omit the parameter name when running a command. However, this only works if you’re using sequential parameters.

For instance, Invoke-FalconRTR works as expected in this example because `-BaseCommand` (position 1), `-Arguments` (position 2) and `-HostIds` (position 3) are all defined:

```powershell
Invoke-FalconRTR ls C:\Windows <id>, <id>
```

If `-Arguments` is _not_ included, this no longer works as PowerShell (or the API, depending on the context) thinks that `-HostIds` is supposed to be the value for `-Arguments`:

```powershell
Invoke-FalconRTR getsid <id>, <id>
```

# -All
The `-All` switch reads the pagination information in an API response and repeats requests to that API until all the available results are retrieved. Using this parameter allows you to ignore the `offset` and `after` fields and have PSFalcon handle the gathering of additional results.

However, it is important to note that the CrowdStrike APIs were not designed to "retrieve all data". If you exceed the maximum limit of a particular API, it is best to modify your command using the `-Filter` parameter to ensure that your next attempts will succeed. Using a filter will allow you to break your results into smaller groups and use those groups to retrieve all the available results.

# -Detailed
If a PSFalcon command returns "identifiers", you can use the `-Detailed` switch to pass the identifiers back to the command and retrieve more detailed information. For example, running `Get-FalconHost` will retrieve host identifiers, but using `Get-FalconHost -Detailed` is the same as running two commands (which outputs the identifiers, plus information about the hosts).

```powershell
$Ids = Get-FalconHost
Get-FalconHost -Ids $ids
```

The `-Detailed` parameter will also break up the secondary command into appropriately sized groups, avoiding errors when retrieving details about large numbers of identifiers.

# Debug and Verbose

Each command was written as an [advanced function](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7) which enables support for common PowerShell parameters, including:

* `-Verbose`: Provides more explicit information during a request
* `-Debug`: Displays the raw JSON content of a request and a response

Using either of these parameters can help you understand the work PSFalcon does behind the scenes to properly format your requests and the responses.