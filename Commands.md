# List available commands
After importing the module you can view the list of commands provided with PSFalcon:
```powershell
Get-Command -Module PSFalcon
```
# Using commands
## PSFalcon v2.1+
Information about PSFalcon commands and their parameters is available using the PowerShell `Get-Help` command. Using the `-Examples`, `-Detailed` or `-Full` parameter(s) provides additional information.
```powershell
Get-Help Request-FalconToken
```
## PSFalcon v2.0
Because PSFalcon uses dynamic parameters, the traditional PowerShell `Get-Help` command doesn't show parameters that can be used with PSFalcon commands. Instead, use `<command> -Help` to call a custom function that displays information about the available parameters and a basic description of their use.
```powershell
PS> Request-FalconToken -Help

## Request an OAuth2 access token

  -ClientId [String]
    OAuth2 API client identifier
      Position : 1
      Pattern : \w{32}

  -ClientSecret [String]
    OAuth2 API client secret
      Position : 2
      Pattern : \w{40}

  -Cloud [String]
    Destination cloud
    Enum : eu-1, us-gov-1, us-1, us-2  
    Position : 3

  -MemberCid [String]
    Child environment to use for authentication in multi-CID configurations
      Position : 4
      Pattern : \w{32}
```
# Command examples
* [Cloud Workload Discovery](https://github.com/CrowdStrike/psfalcon/wiki/Cloud-Workload-Discovery)
* [Detections and Incidents](https://github.com/CrowdStrike/psfalcon/wiki/Detections-and-Incidents)
* [Event Streams](https://github.com/CrowdStrike/psfalcon/wiki/Event-Streams)
* [Falcon Complete Dashboards](https://github.com/CrowdStrike/psfalcon/wiki/Falcon-Complete-Dashboards)
* [Falcon X Recon](https://github.com/CrowdStrike/psfalcon/wiki/Falcon-X-Recon)
* [Firewall Management](https://github.com/CrowdStrike/psfalcon/wiki/Firewall-Management)
* [Flight Control](https://github.com/CrowdStrike/psfalcon/wiki/Flight-Control)
* [Horizon](https://github.com/CrowdStrike/psfalcon/wiki/Horizon)
* [Hosts and Host Groups](https://github.com/CrowdStrike/psfalcon/wiki/Hosts-and-Host-Groups)
* [Installation Tokens](https://github.com/CrowdStrike/psfalcon/wiki/Installation-Tokens)
* [MalQuery](https://github.com/CrowdStrike/psfalcon/wiki/MalQuery)
* [OverWatch Dashboards](https://github.com/CrowdStrike/psfalcon/wiki/OverWatch-Dashboards)
* [Policies](https://github.com/CrowdStrike/psfalcon/wiki/Policies)
* [Real-time Response](https://github.com/CrowdStrike/psfalcon/wiki/Real-time-Response)
* [Sandbox and QuickScan](https://github.com/CrowdStrike/psfalcon/wiki/Sandbox-and-QuickScan)
* [Sensor Installers](https://github.com/CrowdStrike/psfalcon/wiki/Sensor-Installers)
* [Spotlight](https://github.com/CrowdStrike/psfalcon/wiki/Spotlight)
* [Threat Intelligence](https://github.com/CrowdStrike/psfalcon/wiki/Threat-Intelligence)
* [Users and Roles](https://github.com/CrowdStrike/psfalcon/wiki/Users-and-Roles)
* [Zero Trust Assessment](https://github.com/CrowdStrike/psfalcon/wiki/Commands#zero-trust-assessment-1)

# Zero Trust Assessment
## Retrieving Zero Trust Assessment data by host
```powershell
Get-FalconZTA -Ids <id>, <id>
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/156/zero-trust-assessment-apis)._