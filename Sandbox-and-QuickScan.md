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
## Download reports, IOC packs, and PCAP files
### Download a summary
TO_DO
### Download a report
TO_DO
### Download a strict IOC pack
TO_DO
### Find malware samples or sandbox reports
TO_DO
### Check your submission quota
TO_DO

_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/92/falcon-x-apis)._