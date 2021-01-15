## Command List
After importing the module you can view the list of commands provided with PSFalcon:

```powershell
Get-Command -Module PSFalcon
```

## Command-based Help

Because PSFalcon uses dynamic parameters, the traditional PowerShell `Get-Help` command doesn't show parameters that can be used with PSFalcon commands. Instead, use `<command> -Help` to call a custom function that displays information about the available parameters and a basic description of their use.

## Positional Parameters

Most PSFalcon commands have positional parameters (listed when using -Help), which means that you are able to omit the parameter name when running a command. However, this only works if you’re using sequential parameters.

For instance, Invoke-FalconRTR works as expected in this example because `-BaseCommand` (position 1), `-Arguments` (position 2) and `-HostIds` (position 3) are all defined:
```powershell
Invoke-FalconRTR ls C:\Windows <id>, <id>
```

If `-Arguments` is _not_ included, this no longer works as PowerShell (or the API, depending on the context) thinks that `-HostIds` is supposed to be the value for `-Arguments`:

```powershell
Invoke-FalconRTR getsid <id>, <id>
```

## Common PSFalcon Parameters

### All
The -All switch reads the pagination information in an API response and repeats requests to that API until all the available results are retrieved. Using this parameter allows you to ignore the “offset” and “after” fields and have PSFalcon handle the requests.

It is important to note that, in general, the CrowdStrike APIs were not designed to “retrieve all data”. Some APIs will hit a maximum limit (usually around 10,000 results, sometimes as high as 150,000). If you exceed these limits, it is best to modify your command using the -Filter parameter to ensure that your next attempts will succeed.
Detailed
If a PSFalcon command returns “identifiers”, you can use the -Detailed switch to pass the identifiers back to the command and retrieve more detailed information. For example, running Get-FalconHost will retrieve host identifiers, but Get-FalconHost -Detailed is the same as running two commands (which outputs the identifiers, plus information about the hosts).

$Ids = Get-FalconHost
Get-FalconHost -Ids $ids

The -Detailed parameter will also break up the secondary command into appropriately sized groups, ensuring that no errors occur when retrieving details.
Common PowerShell parameters
Each command was written as an advanced function which enables support for common PowerShell parameters, including:

-Verbose	Provides more explicit information during a request
-Debug	Displays the raw JSON content of a request and a response
Using either of these parameters can help you understand the work PSFalcon does behind the scenes to properly format your requests and the responses.
Filtering and the Falcon Query Language
Many PSFalcon commands support the use of Falcon Query Language (“FQL”) statements using the -Filter parameter. However, it is important to keep in mind:

Available FQL filters will vary between APIs, and are not determined by PSFalcon
Each FQL filter and value may be case-sensitive

Values in an FQL statement tend to either be restricted to null, true, false, an integer or a string (description, date or time, etc). 

The simplest FQL statements require a single condition and value. For instance, to find the host identifier for a device with the hostname “ONE”, use the following filter:
Get-FalconHost -Filter "hostname:'ONE'"

Additional conditions and values can be added using the proper operator.

The following filter example will retrieve the host identifier for a device that has a hostname of “ONE” AND is running Windows:
Get-FalconHost -Filter "hostname:'ONE'+platform_name:'Windows'"

To find host identifiers for devices that are named “ONE” OR “TWO”:
Get-FalconHost -Filter "hostname:'ONE',hostname:'TWO'"

Multiple conditions can be used to retrieve more complex results. The following filter lists host identifiers for devices that are named “ONE” AND are running Windows OR IS NOT named “TWO” AND has been seen online within the last two days:
Get-FalconHost -Filter "(hostname:'ONE'+platform_name:'Windows'),(hostname:!'TWO'+last_seen:>'Last 2 days')"

NOTE: 'Last 2 days' is not a valid FQL value when submitted via API. PSFalcon looks for a relative date string like “last <integer> hour(s)/day(s)” and automatically converts it into an RFC3339 date string (UTC).

For example, at exactly 14:00 hours (Pacific Standard Time) on November 10, 2020 if you attempted to use Get-FalconHost with the following filter:
Get-FalconHost -Filter "last_seen:>'Last 2 days'" -Verbose

PSFalcon converts your filter to the following value (seen through the use of the -Verbose parameter):
VERBOSE: [Get-Query] filter=last_seen:>'2020-11-10T22:00:00.0000000Z'
