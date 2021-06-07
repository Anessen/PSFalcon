## Submit a file for analysis
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
## Submit an archive file for analysis
TO_DO
## Analyze large volumes of files with Falcon QuickScan
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
## View sandbox reports
### View a summary-level sandbox report
```powershell
Get-FalconReport -Ids <id>, <id> -Summary
```
### View a sandbox report
```powershell
Get-FalconReport -Ids <id>, <id>
```
## Download artifacts
**NOTE**: The identifiers needed to download artifacts can be found in a sandbox report.
```powershell
$Report = Get-FalconReport -Ids <id>
```
### Download a strict IOC pack
```powershell
Receive-FalconArtifact -Id $Report.ioc_report_strict_csv_artifact_id -Path .\ioc_report_strict_csv_artifact_id.csv
```
## Check your Sandbox submission quota
```powershell
Get-FalconSubmissionQuota
```
## Check your QuickScan submission quota
```powershell
Get-FalconQuickScanQuota
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/92/falcon-x-apis)._