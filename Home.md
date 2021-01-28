# Overview
### [Installation](https://github.com/CrowdStrike/psfalcon/wiki/Installation)
* Downloading and installing the module using the PowerShell Gallery or GitHub
* Importing the module
* Basic troubleshooting and bug reports
### [Commands](https://github.com/CrowdStrike/psfalcon/wiki/Commands)
* Basic command information and finding help
### [Parameters](https://github.com/CrowdStrike/psfalcon/wiki/Parameters)
* Common parameters and result pagination
### [Authentication](https://github.com/CrowdStrike/psfalcon/wiki/Authentication)
* Requesting and revoking OAuth2 access tokens, switching cloud environments, and 'child' CIDs
### [Filtering and the Falcon Query Language](https://github.com/CrowdStrike/psfalcon/wiki/Filtering-and-the-Falcon-Query-Language)
* Using the Falcon Query Language to limit results and combining multiple filter conditions and values
### [CSV Output](https://github.com/CrowdStrike/psfalcon/wiki/CSV-Output)
* Converting results to CSV using `Export-FalconReport`
# Using Commands
### [Custom IOCs](https://github.com/CrowdStrike/psfalcon/wiki/Custom-IOCs)
* Create, find, modify and delete Custom Indicators of Compromise
### [Cloud Workload Discovery](https://github.com/CrowdStrike/psfalcon/wiki/Cloud-Workload-Discovery)
* Register and list cloud accounts and settings for Cloud Workload Discovery
### [Detections and Incidents](https://github.com/CrowdStrike/psfalcon/wiki/Detections-and-Incidents)
* Find or modify detections and incidents, including assignment to users, status changes and hiding detections
* Find CrowdScore values
### [Event Streams](https://github.com/CrowdStrike/psfalcon/wiki/Event-Streams)
* Initiate and view Event Streams
* Capture sample of event data
### [Firewall Management](https://github.com/CrowdStrike/psfalcon/wiki/Firewall-Management)
* Create, find, modify and delete Falcon Firewall Management rule groups and rules
* Find information about rule groups, rules and related Firewall Management properties
### [Horizon](https://github.com/CrowdStrike/psfalcon/wiki/Horizon)
* Create, find, modify and delete cloud accounts for Cloud Security Posture Management using Falcon Horizon
* Review default Falcon Horizon settings and scan schedules
### [Hosts and Host Groups](https://github.com/CrowdStrike/psfalcon/wiki/Hosts-and-Host-Groups)
* Find information about Hosts and contain or hide them
* Create, find, modify, delete and add or remove members from Host Groups
### [Installation Tokens](https://github.com/CrowdStrike/psfalcon/wiki/Installation-Tokens)
* Create, find, modify and delete installation tokens to restrict sensor installations.
### [MalQuery](https://github.com/CrowdStrike/psfalcon/wiki/MalQuery)
* Perform searches and YARA hunts in Falcon MalQuery
* Download malware samples from Falcon MalQuery
### [Policies](https://github.com/CrowdStrike/psfalcon/wiki/Policies)
* Create, find, modify and delete Device Control, Firewall Management, Prevention, Sensor Update and Real-time Response policies
* Assign or remove Host Groups from policies
### [Real-time Response](https://github.com/CrowdStrike/psfalcon/wiki/Real-time-Response)
* Create and find information about Real-time Response sessions with single or batches of devices
* Create, find, modify and delete custom scripts and 'put' files
### [Sandbox and QuickScan](https://github.com/CrowdStrike/psfalcon/wiki/Sandbox-and-QuickScan)
* Upload and submit samples to the Falcon X Sandbox and Falcon QuickScan
* Find information about previous submissions
* Download reports and artifacts
### [Sensor Installers](https://github.com/CrowdStrike/psfalcon/wiki/Sensor-Installers)
* Find and download Falcon Sensor installation packages for different Operating Systems
### [Spotlight](https://github.com/CrowdStrike/psfalcon/wiki/Spotlight)
* Find and get detail about vulnerabilities and remediation information in Falcon Spotlight
### [Threat Intelligence](https://github.com/CrowdStrike/psfalcon/wiki/Threat-Intelligence)
* Find and get detail about threat actors, intelligence indicators, reports and rule sets
* Download reports and rule sets
### [Users and Roles](https://github.com/CrowdStrike/psfalcon/wiki/Users-and-Roles)
* Create, find, modify and delete Falcon console users
* Add or remove user roles
# Basic Scripts
### Detections
* [Assign detections involving a specific file to a user](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#assign-detections-involving-a-specific-file-to-a-user)
* [Find and hide large numbers of detections](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#find-and-hide-large-numbers-of-detections)
### Hosts
* [Find duplicate hosts and hide them](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#find-duplicate-hosts-and-hide-them)
* [Network contain a device by hostname](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#network-contain-a-device-by-hostname)
* [Get host information from multiple Falcon instances](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#get-host-information-from-multiple-falcon-instances)
### Real-time Response
* [Run a command against a group of devices](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#run-a-command-against-a-group-of-devices)
### Sensor Installers
* [Download the installer package assigned to a Sensor Update policy](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#download-the-installer-package-assigned-to-a-sensor-update-policy)
### Vulnerabilities
* [Create a report with additional Host fields](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#create-a-report-with-additional-host-fields)