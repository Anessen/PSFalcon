![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
# List available commands
After importing the module you can view the list of commands provided with PSFalcon:
```powershell
Get-Command -Module PSFalcon
```
# Finding help
_Also see [Parameters](https://github.com/CrowdStrike/psfalcon/wiki/Parameters)._
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
# Converting results to CSV
`Export-FalconReport` translates a [PSCustomObject] into something that is more CSV-friendly and then uses `Export-Csv`.
```powershell
<command> [-Detailed] [-All] | Export-FalconReport -Path .\example.csv
```
If you wish to validate the output before creating a CSV, try:
```powershell
<command> [-Detailed] [-All] | Export-FalconReport
```
# Command examples
**NOTE**: Examples for PSFalcon v2.1+ can be found using:
```powershell
Get-Help <command> -Examples
```
The following examples are for PSFalcon v2.0.x and may include syntax differences compared to v2.1+.
## Falcon Complete Dashboards
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/151/falcon-complete-dashboard-apis)._
### Search for Falcon Complete detection, device collection or incident identifiers
```powershell
Get-FalconCompleteDetection [-All]
```
```powershell
Get-FalconCompleteCollection [-All]
```
```powershell
Get-FalconCompleteIncident [-All]
```
### Display the total number of Falcon Complete detections, device collections or incidents
```powershell
Get-FalconCompleteDetection -Total
```
```powershell
Get-FalconCompleteCollection -Total
```
```powershell
Get-FalconCompleteIncident -Total
```
### Search for Falcon Complete allowlist, blocklist, escalation, or remediation identifiers
```powershell
Get-FalconCompleteAllowlist [-All]
```
```powershell
Get-FalconCompleteBlocklist [-All]
```
```powershell
Get-FalconCompleteEscalation [-All]
```
```powershell
Get-FalconCompleteRemediation [-All]
```
### Display the total number of Falcon Complete allowlist, blocklist, escalation, and remediation tickets
```powershell
Get-FalconCompleteAllowlist -Total
```
```powershell
Get-FalconCompleteBlocklist -Total
```
```powershell
Get-FalconCompleteEscalation -Total
```
```powershell
Get-FalconCompleteRemediation -Total
```
## Falcon X Recon
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/162/falcon-x-recon-apis)._
### Finding a monitoring rule
```powershell
Get-FalconReconRule [-Detailed]
```
### Creating a monitoring rule
```powershell
New-FalconReconRule -Name psfalcon_example -Topic SA_AUTHOR -Filter "author:'example_author'" -Priority low -Permissions private
```
### Creating multiple monitoring rules in a single request
```powershell
$Array = @(
    @{
        name = "psfalcon_example_1"
        topic = "SA_BRAND_PRODUCT"
        filter = "phrase:'psfalcon_example_phrase'"
        priority = "low"
        permissions = "private"
    },
    @{
        name = "psfalcon_example_2"
        topic = "SA_BIN"
        filter = "ccbin:'1234'"
        priority = "medium"
        permissions = "public"
    }
)
New-FalconReconRule -Array $Array
```
### Updating a monitoring rule
```powershell
Edit-FalconReconRule -Id <id> -Name psfalcon_example_updated -Priority medium
```
### Updating multiple monitoring rules in a single request
```powershell
$Array = @(
    @{
        id = <id>
        priority = "high"
    },
    @{
        id = <id>
        priority = "high"
    }
)
Edit-FalconReconRule -Array $Array
```
### Deleting a monitoring rule
```powershell
Remove-FalconReconRule -Ids <id>, <id>
```
### Querying monitoring rule actions
```powershell
Get-FalconReconAction [-Detailed]
```
### Creating email notifications for a monitoring rule
```powershell
New-FalconReconAction -RuleId <rule_id> -Type email -Frequency daily -Recipients user@example.com
```
### Updating email notifications for a monitoring rule
```powershell
Edit-FalconReconAction -Id <id> -Frequency weekly
```
### Deleting email notifications for a monitoring rule
```powershell
Remove-FalconReconAction -Id <id>
```
### Querying notifications
```powershell
Get-FalconReconNotification
```
### Get simplified data from notifications
```powershell
Get-FalconReconNotification [-Detailed]
```
### Get raw intelligence data from notifications
```powershell
Get-FalconReconNotification -Ids <id>, <id> -Intel
```
### Get data from notifications translated into English
```powershell
Get-FalconReconNotification -Ids <id>, <id> -Translate
```
### Get raw intelligence data from notifications translated into English
```powershell
Get-FalconReconNotification -Ids <id>, <id> -Combined
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
New-FalconQuickScan -Ids <sha256>, <sha256>
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