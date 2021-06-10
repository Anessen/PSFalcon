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
### [Configuration Export and Import](https://github.com/CrowdStrike/psfalcon/wiki/Configuration-Export-and-Import)
* Export configured items from one CID, and restore or re-create them in the same or different CID(s)
### [CSV Output](https://github.com/CrowdStrike/psfalcon/wiki/CSV-Output)
* Converting results to CSV using `Export-FalconReport`
# Using Commands
### [Cloud Workload Discovery](https://github.com/CrowdStrike/psfalcon/wiki/Cloud-Workload-Discovery)
* Register and list cloud accounts and settings for Cloud Workload Discovery
### [Detections and Incidents](https://github.com/CrowdStrike/psfalcon/wiki/Detections-and-Incidents)
* Find or modify detections and incidents, including assignment to users, status changes and hiding detections
* Find CrowdScore values
### [Event Streams](https://github.com/CrowdStrike/psfalcon/wiki/Event-Streams)
* Initiate and view Event Streams
* Capture sample of event data
### [Falcon Complete Dashboards](https://github.com/CrowdStrike/psfalcon/wiki/Falcon-Complete-Dashboards)
* Get information about Falcon Complete activity in your Falcon instance
### [Falcon X Recon](https://github.com/CrowdStrike/psfalcon/wiki/Falcon-X-Recon)
* Create, find, modify and delete monitoring rules
* Create, find, modify and delete email notifications for a monitoring rule
* Find notifications from monitoring rule matches
### [Firewall Management](https://github.com/CrowdStrike/psfalcon/wiki/Firewall-Management)
* Create, find, modify and delete Falcon Firewall Management rule groups and rules
* Find information about rule groups, rules and related Firewall Management properties
### [Flight Control](https://github.com/CrowdStrike/psfalcon/wiki/Flight-Control)
* Create, find, modify and delete CID and User Groups for MSSP-style parent/child configurations
* List child CIDs configured under a parent CID account along with related information
* Assign and remove roles from User Groups to control access to child CIDs
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
### [OverWatch Dashboards](https://github.com/CrowdStrike/psfalcon/wiki/OverWatch-Dashboards)
* Get information about Falcon OverWatch activity across all CrowdStrike customers
### [Policies](https://github.com/CrowdStrike/psfalcon/wiki/Policies)
* Create, find, modify and delete policies
* Assign or remove Host Groups from policies
* Manage policy precedence
* Create, find, modify or delete Machine Learning exclusions
* Create, find, modify or delete Sensor Visibility exclusions
* Find, modify or delete Indicator of Attack (IOA) exclusions
* Create, find, modify or delete Custom Indicators (IOCs)
* Create, find, modify or delete Custom Indicators of Attack
### [Real-time Response](https://github.com/CrowdStrike/psfalcon/wiki/Real-time-Response)
* Create and find information about Real-time Response sessions with single or batches of devices
* Create, find, modify and delete custom scripts and 'put' files
### [Sandbox and QuickScan](https://github.com/CrowdStrike/psfalcon/wiki/Sandbox-and-QuickScan)
* Upload and submit samples to the Falcon X Sandbox and Falcon QuickScan
* Find information about previous submissions
* View reports
* Download artifacts
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
### [Zero Trust Assessment](https://github.com/CrowdStrike/psfalcon/wiki/Zero-Trust-Assessment)
* Retrieve Zero Trust Assessment results by host
# Basic Scripts
### Detections
* [Assign detections involving a specific file to a user](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#assign-detections-involving-a-specific-file-to-a-user)
* [Find and hide large numbers of detections](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#find-and-hide-large-numbers-of-detections)
### Hosts
* [Add a list of hostnames to a host group](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#add-a-list-of-hostnames-to-a-host-group)
* [Hide hosts based on last_seen time](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#hide-hosts-based-on-last_seen-time)
* [Find duplicate hosts and hide them](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#find-duplicate-hosts-and-hide-them)
* [Network contain a device by Hostname](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#network-contain-a-device-by-hostname)
* [Network contain a list of Hostnames from a CSV file](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#network-contain-a-list-of-hostnames-from-a-csv-file)
* [Get host information from multiple Falcon instances](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#get-host-information-from-multiple-falcon-instances)
### Host Groups
* [Verify that a list of Host Groups exist within Child CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#verify-that-a-list-of-host-groups-exist-within-child-cids)
### Policies
* [Modify all Sensor Visibility Exclusions to include an additional Host Group](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#modify-all-sensor-visibility-exclusions-to-include-an-additional-host-group)
* [Assign a list of Host Group names to a specific Policy Id within a list of Child CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#assign-a-list-of-host-group-names-to-a-specific-policy-id-within-a-list-of-child-cids)
* [Output a list of assigned Host Groups for designated Policy ids within child CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#output-a-list-of-assigned-host-groups-for-designated-policy-ids-within-child-cids)
### Real-time Response
* [Run a command against a group of devices](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#run-a-command-against-a-group-of-devices)
* [Upload and execute a local script](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#upload-and-execute-a-local-script)
### Sensor Installers
* [Download the installer package assigned to a Sensor Update policy](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#download-the-installer-package-assigned-to-a-sensor-update-policy)
### Threat Intelligence
* [Export domain and IP indicators updated within the last week to CSV](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#export-domain-and-ip-indicators-updated-within-the-last-week-to-csv)
### Vulnerabilities
* [Create a report with additional Host fields](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#create-a-report-with-additional-host-fields)