## Register an AWS account
```powershell
New-FalconHorizonAwsAccount -AccountId <id>
```
### Generate an AWS Cloudformation link
```powershell
$Link = Get-FalconHorizonAwsLink
```
**NOTE**: A link will not be generated if an OrganizationId was included when registering your AWS account.

The link must be visited with your browser to complete the registration process. The PowerShell command `Start-Process` will launch your default browser:
```powershell
Start-Process $Link.url
```
### Check that the AWS account was correctly provisioned
```powershell
Get-FalconHorizonAwsAccount -Ids <id>
```
A properly provisioned account will display status: `Event_DiscoverAccountStatusOperational`.
### Deprovision an AWS account
```powershell
Remove-FalconHorizonAwsAccount -Ids <id>
```
## Register an AWS organizational account
```powershell
New-FalconHorizonAwsAccount -AccountId <id> -OrganizationId <id>
```
### Generate an AWS Cloudformation script
```powershell
Receive-FalconHorizonAwsScript -Path $pwd\aws_provision.sh
```
**NOTE**: The script must be run using [AWS CLI Version 2](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html).
### Check that the AWS account was correctly provisioned
```powershell
Get-FalconHorizonAwsAccount -Ids <id>
```
A properly provisioned account will display status: `Event_DiscoverAccountStatusOperational`.
### Deprovision an AWS organization
```powershell
Remove-FalconHorizonAwsAccount -OrganizationIds <id>
```
## Register an Azure account
```powershell
New-FalconHorizonAzureAccount -SubscriptionId <id> -TenantId <id>
```
### Generate an Azure CLI script
```powershell
Receive-FalconHorizonAzureScript -TenantId <id> -Path $pwd\azure_provision.sh
```
**NOTE**: This script needs to be executed within your Azure Cloud Shell (Bash).
### Check that the Azure account was correctly provisioned
```powershell
Get-FalconHorizonAzureAccount -Ids <id>
```
A properly provisioned account will display status: `Event_DiscoverAccountStatusOperational`.
### Update an Azure account
```powershell
Edit-FalconHorizonAzureAccount -Id <id> [-TenantId <id>]
```
### Deprovision an Azure account
```powershell
Remove-FalconHorizonAzureAccount -Ids <id>, <id>
```
## Retrieve a policy
```powershell
Get-FalconHorizonPolicy -Ids <id>, <id>
```
### Retrieving policies by service
```powershell
Get-FalconHorizonPolicy -Service <service_name> [-Detailed]
```
### Updating policy settings
```powershell
Edit-FalconHorizonPolicy -PolicyId 20 -Enabled $true -Severity medium
```
### Retrieving the assessment schedule
```powershell
Get-FalconHorizonSchedule [-CloudPlatform]
```
### Updating the assessment schedule
```powershell
Edit-FalconHorizonSchedule -CloudPlatform aws -ScanSchedule 2h
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/137/falcon-horizon-apis)._