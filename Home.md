# Overview

### [Installation](https://github.com/CrowdStrike/psfalcon/wiki/Installation)
* Downloading and installing the module using the PowerShell Gallery or GitHub

### [Importing](https://github.com/CrowdStrike/psfalcon/wiki/Importing)
* Loading the module at the beginning of a PowerShell session or script

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

### [Detections and Incidents](https://github.com/CrowdStrike/psfalcon/wiki/Detections-and-Incidents)
* Find or modify detections and incidents, including assignment to users, status changes and hiding detections
* Find CrowdScore values

### [Discover for Cloud](https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud)
* Register and find cloud accounts for cloud workload discovery in Falcon Discover for Cloud
* Review global Falcon Discover for Cloud settings

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
* [Assign specific detections to a user](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#assign-specific-detections-to-a-user)

### Hosts
* [Find duplicate hosts and hide them](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#find-duplicate-hosts-and-hide-them)
* [Network contain a device by hostname](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#network-contain-a-device-by-hostname)
* [Get host information from multiple Falcon instances](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#get-host-information-from-multiple-falcon-instances)