# List available commands
After importing the module you can view the list of commands provided with PSFalcon:
```powershell
Get-Command -Module PSFalcon
```
# Finding help
## PSFalcon v2.1+
Information about PSFalcon commands and their parameters is available using the PowerShell `Get-Help` command. Using the `-Examples`, `-Detailed` or `-Full` parameter(s) provides additional information.
```powershell
Get-Help Request-FalconToken
```
## PSFalcon v2.0.x
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
**NOTE**: Examples for PSFalcon v2.1+ can be found using:
```powershell
Get-Help <command> -Examples
```
The following examples are for PSFalcon v2.0.x and may include syntax differences compared to v2.1+.
## Hosts and host groups
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/84/host-and-host-group-management-apis)._
### Hosts that match an AWS Instance ID
```powershell
Get-FalconHost -Filter "instance_id:'<instance_id>'" [-Detailed] [-All]
```
### Finding all Windows hosts
```powershell
Get-FalconHost -Filter "platform_name:'Windows'" [-Detailed] [-All]
```
### Finding hosts based on multiple criteria
```powershell
Get-FalconHost -Filter "product_type_desc:'Workstation'+status:'normal'+platform_name:['Windows','Mac']+last_seen:>='2020-07-04'" [-Detailed] [-All]
```
### Retrieving a list of the first 100 hosts in your environment
```powershell
Get-FalconHost [-Detailed]
```
### Getting information about hosts
```powershell
Get-FalconHost -Ids <id>, <id>
```
### Containing and lifting containment on hosts
```powershell
Invoke-FalconHostAction -Name contain -Ids <id>, <id>
```
```powershell
Invoke-FalconHostAction -Name lift_containment -Ids <id>, <id>
```
### Deleting and restoring hosts
```powershell
Invoke-FalconHostAction -Name hide_host -Ids <id>, <id>
```
```powershell
Invoke-FalconHostAction -Name unhide_host -Ids <id>, <id>
```
### Finding hosts that have been deleted
```powershell
Get-FalconHost -Hidden [-Detailed] [-All]
```
### Create a static host group
```powershell
New-FalconHostGroup -GroupType static -Name 'Test Group 45' -Description 'A demo group'
```
### Assigning hosts to a static host group
```powershell
Invoke-FalconHostGroupAction -Name add-hosts -Id <id> -HostIds <id>, <id>
```
### Create a dynamic host group
```powershell
New-FalconHostGroup -GroupType dynamic -Name Dynamic_Group -AssignmentRule "hostname:'*-BL',hostname:'*-DT'"
```
### Finding host groups
```powershell
Get-FalconHostGroup [-Detailed] [-All]
```
### Deleting host groups
```powershell
Remove-FalconHostGroup -Ids <id>, <id>
```
## Installation tokens
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/120/Installation-token-APIs)._
### View installation token settings
```powershell
Get-FalconInstallTokenSettings
```
### Create installation tokens
```powershell
New-FalconInstallToken -Label "My Token" -ExpiresTimestamp "2021-12-31T00:00:00Z"
```
### Find installation tokens
```powershell
Get-FalconInstallToken [-Detailed] [-All]
```
### Get information about an installation token
```powershell
Get-FalconInstallToken -Ids <id>, <id>
```
### Modify an installation token
```powershell
Edit-FalconInstallToken -Ids <id>, <id> -Revoked $true
```
```powershell
Edit-FalconInstallToken -Ids <id> -Label "Token no expiration" -ExpiresTimestamp null
```
### Delete installation tokens
```powershell
Remove-FalconInstallToken -Ids <id>, <id>
```
### View installation token audit events
```powershell
Get-FalconInstallTokenEvent [-Detailed] [-All]
```
### Get information about an installation token audit event
```powershell
Get-FalconInstallTokenEvent -Ids <id>, <id>
```
## MalQuery
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/113/malquery-apis)._
### Perform a simple YARA search for a specific hash
**NOTE**: PSFalcon has a custom command named `Search-FalconMalQueryHash` which will run a simple YARA-based hash search to find a SHA256 value.
```powershell
Search-FalconMalQueryHash -Sha256 <sha256>
```
### Schedule a hunt
```powershell
Invoke-FalconMalQuery -FilterFiletypes pe32 -MaxSize 1200KB -FilterMeta sha256, label, family -YaraRule "rule CrowdStrike_16142_01 : wiper { strings: $ = { 41 61 43 63 64 44 65 46 66 47 68 69 4B 4C 6C 4D 6D 6E 4E 6F 4F 70 50 72 52 73 53 54 74 55 75 56 76 77 57 78 79 5A 7A 33 32 2E 5C 45 62 67 6A 48 49 20 5F 59 51 42 3A 22 2F 40 } condition: all of them and filesize < 800KB }"
```
### Perform an exact search
```powershell
Invoke-FalconMalQuery -FilterMeta sha256, type, size -FilterFiletypes pe32, pe64 -MaxSize 1200KB -MinDate 2017/01/01 -Limit 20 -Type hex -Value 8948208b480833ca33f989502489482889782c8bd7
```
### Perform a fuzzy search
```powershell
Invoke-FalconMalQuery -Limit 3 -Type ascii -Value ".8@bVn7r&k" -Fuzzy
```
### Check the status of a search
```powershell
Get-FalconMalQuery -Ids <id>, <id>
```
### Retrieve MalQuery sample metadata
```powershell
Get-FalconMalQuerySample -Ids <sha256>, <sha256>
```
### Download a MalQuery sample
```powershell
Receive-FalconMalQuerySample -Id <sha256> -Path .\infected.exe
```
### Download an archive of multiple MalQuery samples
```powershell
$Request = Group-FalconMalQuerySample -Samples <sha256>, <sha256>
Receive-FalconMalQuerySample -Id $Request.reqid -Path .\infected.zip
```
### Check your MalQuery quota
```powershell
Get-FalconMalQueryQuota
```
## OverWatch Dashboards
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/155/falcon-overwatch-dashboard-apis)._
### Getting the total number of Falcon OverWatch detections for the past 48 hours
```powershell
Get-FalconOverWatchDetection -Filter "detect_time:>'now-48h'"
```
### Getting the total number of Falcon OverWatch events that occurred across all customers
```powershell
Get-FalconOverWatchEvent -Filter "total_count:>1"
```
### Getting the total number of Falcon OverWatch incidents for the past 48 hours
```powershell
Get-FalconOverWatchIncident -Filter "detect_time:>'now-48h'"
```
## Policies
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/85/detection-and-prevention-policies-apis)._
### Create a Prevention policy
```powershell
$Settings = @(
    @{
        id = "AdditionalUserModeData"
        value = @{
            enabled = $true
        }
    },
    @{
        id = "EndUserNotifications"
        value = @{
            enabled = $true
        }
    },
    @{
        id = "CloudAntiMalware"
        value = @{
            detection = "MODERATE"
            prevention = "MODERATE"
        }
    }
)
New-FalconPreventionPolicy -PlatformName Windows -Name "Demo Policy" -Description "This is a demo policy" -Settings $Settings
```
### Assign a host group to a Prevention policy
```powershell
Invoke-FalconPreventionPolicyAction -ActionName add-host-group -Id <id> -GroupId <id>
```
### Set Prevention policy precedence
**NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in precedence order.
```powershell
Set-FalconPreventionPrecedence -PlatformName Windows -Ids <id>, <id>
```
### Get all Prevention policies
```powershell
Get-FalconPreventionPolicy -All [-Detailed]
```
### Finding the uninstallation token for a host
```powershell
Get-FalconUninstallToken -DeviceId <id>
```
### Finding the maintenance token that applies to any host within a given policy
```powershell
Get-FalconUninstallToken -DeviceId MAINTENANCE
```
### Create Machine Learning exclusions
```powershell
New-FalconMLExclusion -Value '/foo' -ExcludedFrom blocking, extraction -GroupIds all -Comment 'creating foo'
```
### Find Machine Learning exclusions
```powershell
Get-FalconMLExclusion [-Detailed] [-All]
```
### Modify Machine Learning exclusions
```powershell
Edit-FalconMLExclusion -Id <id> -Value '/foo*'
```
### Delete Machine Learning exclusions
```powershell
Remove-FalconMLExclusion -Ids <id>, <id>
```
### Create Sensor Visibility exclusions
```powershell
New-FalconSVExclusion -Value '/foo' -GroupIds all -Comment 'creating'
```
### Find Sensor Visibility exclusions
```powershell
Get-FalconSVExclusion [-Detailed] [-All]
```
### Modify Sensor Visibility exclusions
```powershell
Edit-FalconSVExclusion -Id <id> -Value '/foochanged*'
```
### Delete Sensor Visibility exclusions
```powershell
Remove-FalconSVExclusion -Ids <id>, <id>
```
### Modify IOA exclusions
```powershell
Edit-FalconIOAExclusion -Id <id> -ImagePath '.*\\Windows\\System32\\choice1\.exe'
```
### Find IOA exclusions
```powershell
Get-FalconIOAExclusion [-Detailed]
```
### Delete IOA exclusions
```powershell
Remove-FalconIOAExclusion -Ids <id>, <id>
```
### Find custom IOA rule types
```powershell
Get-FalconIOAType [-Detailed]
```
### Find custom IOA severities
```powershell
Get-FalconIOASeverity [-Detailed]
```
### Find custom IOA platforms
```powershell
Get-FalconIOAPlatform [-Detailed]
```
### Create custom IOA rule groups
```powershell
New-FalconIOAGroup -Platform mac -Name newRuleGroup -Description "My new mac rule group"
```
### Modify custom IOA rule groups
```powershell
$Current = Get-FalconIOAGroup -Filter "name:'newRuleGroup'" -Detailed
Edit-FalconIOAGroup -Id $Current.id -Name "updatedRuleGroup" -Enabled $true -RulegroupVersion $Current.version -Description "My updated mac rule group" -Comment "Updated using PSFalcon"
```
### Find custom IOA rule groups
```powershell
Get-FalconIOAGroup [-Detailed]
```
### Delete custom IOA rule groups
```powershell
Remove-FalconIOAGroup -Ids <id>, <id>
```
### Create custom IOA rules
```powershell
$Group = Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'" -Detailed
$FieldValues = @{
    label = 'Grandparent Image Filename'
    name = 'GrandparentImageFilename'
    type = 'excludable'
    values = @(
        @{
            label = 'include'
            value = '.+bug.exe'
        }
    )
}
New-FalconIOARule -RulegroupId $Group.id -Name "BugRule" -PatternSeverity critical -RuletypeId 5 -DispositionId 30 -FieldValues $FieldValues
```
### Modify custom IOA rules
```powershell
$Group = Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'" -Detailed
$RuleUpdates = @(
    @{
        name = 'BugRule'
        pattern_severity = 'critical'
        enabled = $true
        description = 'Stops the bug'
        disposition_id = 30
        instance_id = '1'
        field_values = @(
            @{
                label = 'Grandparent Image Filename'
                name = 'GrandparentImageFilename'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.+updatebug.exe'
                    }
                )
            },
            @{
                label = 'Grandparent Command Line'
                name = 'GrandparentCommandLine'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            },
            @{
                label = 'Parent Image Filename'
                name = 'ParentImageFilename'
                type = 'excludable'
                values = @(
                      @{
                          label = 'include'
                          value = '.*'
                       }
                  )
            },
            @{
                label = 'Parent Command Line'
                name = 'ParentCommandLine'
                type = 'excludable'
                values = @(
                    @{
                         label = 'include'
                         value = '.*'
                    }
                )
            },
            @{
                label = 'Image Filename'
                name = 'ImageFilename'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            },
            @{
                label = 'Command Line'
                name = 'CommandLine'
                type = 'excludable'
                values = @(
                    @{
                        label = 'include'
                        value = '.*'
                    }
                )
            }
        )
    }
)
Edit-FalconIOARule -RulegroupId $Group.id -RulegroupVersion $Group.version -RuleUpdates $RuleUpdates -Comment "Updated using PSFalcon"
```
### Find custom IOA rules
```powershell
Get-FalconIOARule [-Detailed]
```
### Delete custom IOA rules
```powershell
Remove-FalconIOARule -RulegroupId <id> -Ids <id>, <id>
```
### Validating field values
```powershell
$Fields = @(
    @{
        label = 'Grandparent Image Filename'
        name = 'GrandparentImageFilename'
        type = 'excludable'
        values = @(
            @{
                label = 'include'
                value = '.+attacker.exe'
            }
        )
    }
)
Test-FalconIOARule -Fields $Fields
```
### Find custom IOA rule groups matching a query
```powershell
Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'+platform:'mac'" -Detailed
```
### Find custom IOA rule group identifiers matching a query
```powershell
Get-FalconIOAGroup -Filter "name:'updatedRuleGroup'+platform:'mac'"
```
### Find a custom IOA rule identifier by name within a rule group
```powershell
Get-FalconIOARule -Filter "id:'<id>'+rules.name:'BugRule'" [-Detailed] [-All]
```
### Creating a domain indicator
```powershell
New-FalconIOC -Type domain -Value example01.com -Action detect -Severity medium -Description 'test description' -Platforms windows, mac, linux -Tags test_tag -HostGroups <host_group_id>, <host_group_id> -Expiration 2021-05-01
```
### Creating multiple indicators in a single request
```powershell
$Array = @(
    @{
        type = "domain"
        value = "example01.com"
        action = "detect"
        severity = "medium"
        description = "test description"
        platforms = @("windows", "mac", "linux")
        tags = @("test_tag")
        host_groups = @("<id>")
    },
    @{
        type = "sha256"
        value = "a88787d8ff144c502c7f5cffaafe2cc588d86079f9de88304c26b0cb99ce91cc"
        source = "bd20201216"
        filename = "iexplore.exe"
        action = "prevent"
        severity = "high"
        description = "test block description"
        platforms = @("windows")
        tags = @("test_tag", "test_tag2")
        applied_globally = $true
    }
)
New-FalconIOC -Array $Array
```
### Finding domain indicator identifiers
```powershell
Get-FalconIOC -Filter "type:'domain'
```
### Retrieving details about an indicator by its identifier
```powershell
Get-FalconIOC -Ids <id>, <id>
```
### Retrieving indicator details in large batches
```powershell
Get-FalconIOC -Filter "type:'domain'+tags:'MalDomain_20201215'+tags:'domains_mac'" -Detailed
```
### Updating an indicator by identifier
```powershell
Edit-FalconIOC -Id <id> -Source testSource -Action detect -Severity low -Description 'test description update' -Platforms windows -Tags test_tag2 -HostGroups all -Expiration '2021-05-01T12:00:00Z'
```
### Deleting indicators by identifier
```powershell
Remove-FalconIOC -Ids <id>, <id>
```
## Real-time Response
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/90/real-time-response-apis)._
### Invoke-FalconRtr
PSFalcon has a custom command named `Invoke-FalconRtr` that is designed to perform all the necessary steps to initiate a session with one or more hosts, send a command and output the results.

**This command is not designed for a multi-step Real-time Response workflow** and will negatively impact certain operations.

For instance, if you were to `cd` into a directory and attempt to `put` a file by running `Invoke-FalconRtr` twice, `Invoke-FalconRtr` will reset back to the root of your system drive between the `cd` and `put` commands, causing the file to be placed in the wrong directory.
```powershell
Invoke-FalconRtr -Command ls -Arguments C:\Windows -HostIds <id>, <id>
```
If the hosts you're targeting are currently offline, you can add your Real-time Response commands to the "offline queue" using the `-QueueOffline` parameter.
```powershell
Invoke-FalconRtr -Command runscript -Arguments "-CloudFile='HelloWorld'" -HostIds <id>, <id> -QueueOffline $true
```
If you find that your script needs to be more complex, you can follow the instructions below to create a custom Real-time Response workflow with multiple commands.
**NOTE**: PSFalcon includes commands for each Real-time Response permission level.
* `Invoke-FalconCommand`, `Confirm-FalconCommand`
* `Invoke-FalconResponderCommand`, `Confirm-FalconResponderCommand`
* `Invoke-FalconAdminCommand`, `Confirm-FalconAdminCommand`
### Invoke-FalconDeploy
`Invoke-FalconDeploy` was developed to support mass-deployment of Falcon Forensics. It is designed to upload a file to your ‘Put’ Files library, create a session with target hosts, push the file to those hosts, then execute it and output the results to CSV.

**NOTE**: Because Real-time Response does not interact with logged in users, the executable must be able to be run silently and without user interaction.
```powershell
Invoke-FalconDeploy -HostIds <id>, <id> -Path $pwd\File.exe [-QueueOffline]
```
### Get-FalconQueue
`Get-FalconQueue` will create a CSV file with information about sessions that have pending queued commands or have been created in the last 7 days (by default).
```powershell
Get-FalconQueue [-Days]
```
### Start a batch session with multiple hosts
```powershell
$Batch = Start-FalconSession -HostIds <id>, <id>
```
### Send a command using appropriate permissions
```powershell
Invoke-FalconCommand -Command ls -Arguments C:\Windows -BatchId $Batch.batch_id
```
### Refresh the session to prevent expiration
**NOTE**: Required when you expect to exceed the default batch session expiration time (5 minutes).
```powershell
Update-FalconSession -BatchId $Batch.batch_id
```
### Start a session with a single host
```powershell
$Session = Start-FalconSession -HostId <id>
```
### Send a command using appropriate permissions
```powershell
$Command = Invoke-FalconCommand -Command ls -Arguments C:\Windows -SessionId $Session.session_id
```
### Retrieve command results
```powershell
Confirm-FalconCommand -CloudRequestId $Command.cloud_request_id
```
**NOTE**: This step is important! Without retrieving the results from an issued command, the Real-time Response session may not reflect that actions have taken place. For instance, If you `cd` and don't confirm, you'll stay in your current directory.
### Refresh the session to prevent expiration
**NOTE**: Refreshing the session is required when you expect to exceed the default expiration time (10 minutes).
```powershell
Update-FalconSession -SessionId $Session.session_id
```
### Use Real-time Response to download a file from multiple hosts
```powershell
$Get = Invoke-FalconRTR -Command get -Arguments "C:\example.exe" -HostIds <id>, <id>
```
Once the batch 'get' request has been submitted using `Invoke-FalconRTR`, you can check the status of each `batch_get_cmd_req_id` to see if the file is ready to download.
```powershell
$Confirm = ($Get.batch_get_cmd_req_id | Group-Object).Name | ForEach-Object {
    Confirm-FalconGetFile -BatchGetCmdReqId $_
}
```
The upload from the host has completed once the file has populated `sha256` and `created_at` values. You can use the `sha256` and `session_id` values to download the files, and in the following example, each file will be downloaded and saved in your local directory, using the `sha256` and `aid` values to name the archive.
```powershell
$Confirm | Where-Object { $_.sha256 -and $_.created_at -and $_.session_id } | ForEach-Object {
    $Param = @{
        Sha256 = $_.sha256
        SessionId = $_.session_id
        Path = "$pwd\$($_.aid)_$($_.sha256).7z"
    }
    Receive-FalconGetFile @Param
}
```
You can re-run the previous command examples (`Confirm-FalconGetFile` and `Receive-FalconGetFile`) repeatedly to download additional files as their uploads complete from each individual host.
### Find Real-time Response sessions
**NOTE**: Only sessions created by your OAuth2 API Client will be visible using the following commands.
```powershell
Get-FalconSession [-Detailed] [-All]
```
### Retrieve detail about Real-time Response sessions
**NOTE**: Only sessions created by your OAuth2 API Client will be visible using the following commands.
```powershell
Get-FalconSession -Ids <id>, <id> [-Queue]
```
### Create a new Real-time Response script
```powershell
Send-FalconScript -Path $pwd\hello_world.ps1 -Platform windows -PermissionType group
```
### Find Real-time Response scripts
```powershell
Get-FalconScript [-Detailed] [-All]
```
### Modify Real-time Response scripts
```powershell
Edit-FalconScript -Id <id>
```
### Delete Real-time Response scripts
```powershell
Remove-FalconScript -Ids <id>, <id>
```
### Create a new Real-time Response ‘put’ file
```powershell
Send-FalconPutFile -Path $pwd\File.exe
```
### Find Real-time Response ‘put’ files
```powershell
Get-FalconPutFile [-Detailed] [-All]
```
### Delete Real-time Response ‘put’ files
```powershell
Remove-FalconPutFile -Ids <id>
```
## Sandbox and QuickScan
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/92/falcon-x-apis)._
### Upload files for submission
```powershell
$Sample = Send-FalconSample -Path C:\virus.exe -Filename virus.exe -Comment 'bad file'
```
### Submit an uploaded sample for analysis in a sandbox environment
```powershell
$Submission = New-FalconSubmission -Sha256 $Sample.sha256 -EnvironmentId win7_x86 -SubmitName virus.exe
```
### Check the progress of samples previously submitted for analysis
```powershell
Get-FalconSubmission -Ids $Submission.id
```
### Submit files to QuickScan
**NOTE**: The files submitted for QuickScan must be available via a previous upload using `Send-FalconSample`.
```powershell
New-FalconQuickScan -Samples <sha256>, <sha256>
```
### Search for QuickScans run in the last 7 days
```powershell
Get-FalconQuickScan -Filter "created_timestamp:>'Last 7 days'" [-Detailed]
```
### Retrieve information about a QuickScan
```powershell
Get-FalconQuickScan -Ids <id>
```
### View a summary-level sandbox report
```powershell
Get-FalconReport -Ids <id>, <id> -Summary
```
### View a sandbox report
```powershell
Get-FalconReport -Ids <id>, <id>
```
### Download artifacts
**NOTE**: The identifiers needed to download artifacts can be found in a sandbox report.
```powershell
$Report = Get-FalconReport -Ids <id>
```
### Download a strict IOC pack
```powershell
Receive-FalconArtifact -Id $Report.ioc_report_strict_csv_artifact_id -Path .\ioc_report_strict_csv_artifact_id.csv
```
### Check your Sandbox submission quota
```powershell
Get-FalconSubmissionQuota
```
### Check your QuickScan submission quota
```powershell
Get-FalconQuickScanQuota
```
## Sensor Installers
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/109/sensor-download-apis)._
### Find all available sensor installers for Linux
```powershell
Get-FalconInstaller -Filter "platform:'linux'" [-Detailed] [-All]
```
### Find all available sensor installers for a specific OS version
```powershell
Get-FalconInstaller -Filter "os:'Amazon Linux'" [-Detailed] [-All]
```
### Retrieve detailed information about a specific sensor installer
```powershell
Get-FalconInstaller -Ids <id>
```
### Download a sensor installer
```powershell
Receive-FalconInstaller -Id <id> -Path .\WindowsSensor.exe
```
### Find your Customer ID and Checksum \(CCID\)
```powershell
Get-FalconCCID
```
## Spotlight
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/98/spotlight-apis)._
### Search for vulnerabilities
**NOTE**: The Spotlight API requires the use of a filter when requesting results.
```powershell
Get-FalconVulnerability -Filter "created_timestamp:>'2019-11-25T22:36:12Z'" [-Detailed] [-All]
```
### Get information about specific vulnerabilities
```powershell
Get-FalconVulnerability -Ids <id>, <id>
```
### Get information about specific remediations
```powershell
Get-FalconRemediation -Ids <id>, <id>
```
## Threat Intelligence
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/72/intel-apis)._
### Search for actors
```powershell
Get-FalconActor -Filter "target_countries:'united states'+target_countries:'canada'+target_industries:'government'" [-Detailed] [-All]
```
### Get information about specific actors
```powershell
Get-FalconActor -Ids <id>, <id>
```
### Search for information about actors
```powershell
Get-FalconActor -Filter "target_countries:'united states'+target_countries:'canada'+target_industries:'government'" -Limit 1 -Detailed
```
### Search for indicators
```powershell
Get-FalconIndicator -Filter "type:'domain'" [-Detailed]
```
### Get information about specific indicators
```powershell
Get-FalconIndicator -Ids <id>, <id>
```
### Search for information about indicators
```powershell
Get-FalconIndicator -Filter "last_updated:>=1427846400" -Sort "last_updated|asc" -Detailed [-All]
```
### Search for reports
```powershell
Get-FalconReport -Filter "target_countries:'united states'+target_industries:'government'"
```
### Get information about specific reports
```powershell
Get-FalconReport -Ids <id>, <id>
```
### Search for information about reports
```powershell
Get-FalconReport -Filter "target_countries:'afghanistan'" -Limit 1 -Detailed
```
### Download the latest rule set
```powershell
Receive-FalconRule -Type yara-master -Path $pwd\yara-master.zip
```
### Search for a rule set
```powershell
Get-FalconRule -Filter "type=yara-master&min_created_date_date=1509494400" -Limit 3
```
### Get information about a specific rule set
```powershell
Get-FalconRule -Ids <id>, <id>
```
### Download a specific rule set
```powershell
Receive-FalconRule -Id <id> -Path $pwd\rules.zip
```
## Users and Roles
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/87/users-and-roles-apis)._
### Create a new user
```powershell
New-FalconUser -Username jane.doe@example.com
```
### List all users
```powershell
Get-FalconUser [-Detailed]
```
### Get details on one or more users
```powershell
Get-FalconUser -Ids <id>, <id>
```
### Modify a user
```powershell
Edit-FalconUser -Id <id> -FirstName Jane -LastName Doe
```
### Remove a user
```powershell
Remove-FalconUser -Id <id>
```
### List all available user roles
```powershell
Get-FalconRole [-Detailed]
```
### List roles assigned to a user
```powershell
Get-FalconRole -UserId <id> [-Detailed]
```
### Assign roles to a user
```powershell
Add-FalconRole -Ids <id>, <id> -UserId <id>
```
### Revoke roles from a user
```powershell
Remove-FalconRole -Ids <id>, <id> -UserId <id>
```
## Zero Trust Assessment
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/156/zero-trust-assessment-apis)._
### Retrieving Zero Trust Assessment data by host
```powershell
Get-FalconZTA -Ids <id>, <id>
```