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
# Using commands
**NOTE**: Examples for PSFalcon v2.1+ can be found using:
```powershell
Get-Help <command> -Examples
```
The following examples are for PSFalcon v2.0.x and may include syntax differences compared to v2.1+.
## Real-time Response
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/90/real-time-response-apis)._
**NOTE**: PSFalcon has a custom command named `Invoke-FalconRTR` that is designed to perform all the necessary steps to initiate a session with one or more hosts, send a command and output the results. **This command is not designed for a multi-step Real-time Response workflow** and will negatively impact certain operations. For instance, if you were to `cd` into a directory and attempt to `put` a file by running `Invoke-FalconRTR` twice, `Invoke-FalconRTR` will reset back to the root of your system drive between the `cd` and `put` commands, causing the file to be placed in the wrong directory.
```powershell
Invoke-FalconRTR -Command ls -Arguments C:\Windows -HostIds <id>, <id>
```
If the hosts you're targeting are currently offline, you can add your Real-time Response commands to the "offline queue" using the `-QueueOffline` parameter.
```powershell
Invoke-FalconRTR -Command runscript -Arguments "-CloudFile='HelloWorld'" -HostIds <id>, <id> -QueueOffline $true
```
If you find that your script needs to be more complex, you can follow the instructions below to create a custom Real-time Response workflow with multiple commands.

**NOTE**: PSFalcon includes commands for each Real-time Response permission level.
* `Invoke-FalconCommand`, `Confirm-FalconCommand`
* `Invoke-FalconResponderCommand`, `Confirm-FalconResponderCommand`
* `Invoke-FalconAdminCommand`, `Confirm-FalconAdminCommand`
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
### Use Real-time Response to upload and run an executable
**NOTE**: The command `Invoke-FalconDeploy` was developed to support mass-deployment of Falcon Forensics. It is designed to upload a file to your ‘Put’ Files library, create a session with target hosts, push the file to those hosts, then execute it and output the results to CSV.

**NOTE**: Because Real-time Response does not interact with logged in users, the executable must be able to be run silently and without user interaction.
```powershell
Invoke-FalconDeploy -HostIds <id>, <id> -Path $pwd\File.exe [-QueueOffline]
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
Get-FalconSession -Ids <id>, <id> -Queue
```
### Retrieve detail about queued Real-time Response sessions
**NOTE**: PSFalcon has a custom command named `Get-FalconQueue` which will create a CSV file with information about sessions that have pending queued commands or have been created in the last 7 days (by default). If you wish to get more specific, you can use `Get-FalconSession` to find queued sessions, and the command below to get detailed information.
```powershell
Get-FalconQueue [-Days]
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