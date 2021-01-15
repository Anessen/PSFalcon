[PSFalcon](https://github.com/crowdstrike/psfalcon) is a [PowerShell Module](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7) that lets CrowdStrike Falcon users interact with the CrowdStrike Falcon [OAuth2 APIs](https://assets.falcon.crowdstrike.com/support/api/swagger.html#/) without having extensive knowledge of APIs or PowerShell.

PSFalcon lets you automate tasks and perform actions in large numbers not normally accessible through the Falcon UI. For example, you could use PSFalcon to create scripts that:

* Modify large numbers of detections, incidents, policies or rules
* Utilize Real-time Response to perform an action on many devices at the same time
* Upload or download malware samples or Real-time Response files
* Create/modify configurations for MSSP parent and child environments

# Requirements

* Subscription: Falcon Platform subscriptions that support what you intend to do
* System requirements: PowerShell 5.1+ (Windows), PowerShell 6+ (Linux/MacOS)
* Roles: Falcon [OAuth2 API Client roles](https://falcon.crowdstrike.com/support/api-clients-and-keys) that support what you intend to do

# Installation

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

## Authentication

### Requesting an Authentication Token
During a PowerShell session, you must have a valid OAuth2 token in order to make requests to the CrowdStrike Falcon API endpoints.

If you have already input your credentials, PSFalcon requests a token on your behalf when you issue a command. Otherwise, you must request a token and provide the credentials. You can do this using `Request-FalconToken`, or input your Id/Secret when prompted after issuing a PSFalcon command.

```powershell
Request-FalconToken
ClientId: <string>
ClientSecret: <string>
```

After a valid OAuth2 token is received, it caches with your credentials. Your cached token is checked and refreshed as needed while running PSFalcon commands.

### Revoking an Authentication Token

Authentication tokens expire after 30 minutes. If you wish to revoke an existing token, you can use `Revoke-FalconToken`.

**NOTE**: Revoking a token will also clear your credentials. This is useful if you wish to switch between different Falcon environments.

```powershell
Revoke-FalconToken
```

## Child environments
If you're using an MSSP configuration, you can target specific child environments using the -CID parameter during authentication token requests. Your choice is saved and all requests are sent to that particular CID unless a new Request-FalconToken request is made specifying a new child environment.
Alternate clouds
Authentication token requests are sent to the “us-1“ cloud by default. You may use the -Cloud parameter to choose a different cloud destination.

The accepted hostname values can be viewed using tab auto-completion after entering the -Cloud parameter, or through Request-FalconToken -Help. Your cloud choice is saved and all requests are sent to the chosen cloud unless a new Request-FalconToken request is made specifying a new cloud.
Commands
After importing the module, view the list of commands provided with PSFalcon by using Get-Command -Module PSFalcon.
Command-based help
Because the commands use dynamic parameters, the traditional PowerShell Get-Help command doesn't show parameters that can be used with PSFalcon commands. Instead, use <command> -Help to call a custom function that displays information about the available parameters and a basic description of their use.
Positional parameters
Most PSFalcon commands have positional parameters (listed when using -Help), which means that you are able to omit the parameter name when running a command. However, this only works if you’re using sequential parameters.

For instance, Invoke-FalconRTR works as expected in this example because -BaseCommand (position 1), -Arguments (position 2) and -HostIds (position 3) are all defined:
Invoke-FalconRTR ls C:\Windows <id>, <id>

If -Arguments is not included, this no longer works as the PowerShell (or API, depending on the context) thinks that -HostIds is meant to be -Arguments:
Invoke-FalconRTR getsid <id>, <id>
Common PSFalcon parameters
All
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
