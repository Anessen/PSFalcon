Many PSFalcon commands support the use of [Falcon Query Language](https://falcon.crowdstrike.com/support/documentation/45/falcon-query-language-fql) \("FQL"\) statements using the `-Filter` parameter. However, it is important to keep in mind:

* **_Available FQL filters and their syntax will vary between APIs and are not determined by PSFalcon_**
* Each FQL filter and value may be case-sensitive (exact case, lowercase only, etc.)

Values in an FQL statement tend to either be restricted to `$true`, `$false`, an `integer` or a `string` (description, date or time, etc). 

# Simple Filters
The simplest FQL statements require a single condition and value. For instance, to find the host identifier for a device with the hostname `ONE`, use the following filter:
```powershell
Get-FalconHost -Filter "hostname:'ONE'"
```
Many filters will automatically return partial matches, but you can include wildcards (`*`):
```powershell
Get-FalconHost -Filter "hostname:*'*ONE*'"
```
Using square brackets will restrict results to exact matches (including case):
```powershell
Get-FalconHost -Filter "hostname:['ONE']"
```
# Multiple Values
Additional conditions and values can be added using the proper [operator](https://falcon.crowdstrike.com/support/documentation/45/falcon-query-language-fql#Operators). The following filter example will retrieve the host identifier for a device that has a hostname of `ONE` and is running Windows:
```powershell
Get-FalconHost -Filter "hostname:'ONE'+platform_name:'Windows'"
```
To find host identifiers for devices that are named `ONE` or `TWO`:
```powershell
Get-FalconHost -Filter "hostname:'ONE',hostname:'TWO'"
```
Multiple conditions can be used to retrieve more complex results. The following filter lists host identifiers for devices that are named `ONE` and are running Windows or are not named `TWO` and have been seen online within the last two days:
```powershell
Get-FalconHost -Filter "(hostname:'ONE'+platform_name:'Windows'),(hostname:!'TWO'+last_seen:>'Last 2 days')"
```
**NOTE**: 'Last 2 days' is not a valid FQL value when submitted via API. PSFalcon looks for a relative date string like `last <integer> hour(s)/day(s)` and automatically converts it into an RFC3339 date string \(UTC\).

For example, at exactly 14:00 hours \(Pacific Standard Time\) on November 10, 2020 if you attempted to use `Get-FalconHost` with the following filter:
```powershell
Get-FalconHost -Filter "last_seen:>'Last 2 days'"
```
PSFalcon converts your filter to the following value \(seen through the `Write-Verbose` output\):
```powershell
VERBOSE: [ApiClient.Invoke] ... ?filter=last_seen:>'2020-11-10T22:00:00Z'
```