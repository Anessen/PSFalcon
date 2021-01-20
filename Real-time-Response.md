**NOTE**: PSFalcon has a custom command named `Invoke-FalconRTR` that is designed to perform all the necessary steps to initiate a session with one or more hosts, send a command and output the results. 
```powershell
Invoke-FalconRTR -Command ls -Arguments C:\Windows -HostIds <id>, <id> [-QueueOffline]
```
If you find that your script needs to be more complex, you can follow the instructions below to create a custom Real-time Response workflow with multiple commands.

**NOTE**: PSFalcon includes commands for each Real-time Response permission level.
* `Invoke-FalconCommand`, `Confirm-FalconCommand`
* `Invoke-FalconResponderCommand`, `Confirm-FalconResponderCommand`
* `Invoke-FalconAdminCommand`, `Confirm-FalconAdminCommand`

## Send Real-time Response commands to a batch of hosts
### Start a batch session
```powershell
$Batch = Start-FalconSession -HostIds <id>, <id>
```
### Send a command using appropriate permissions
```powershell
Invoke-FalconCommand -Command ls -Arguments C:\Windows -BatchId $Batch.batch_id
```
### Refresh the session to prevent expiration
**NOTE**: Required when you expect to exceed the default session expiration time (5 minutes).
```powershell
Update-FalconSession -BatchId $Batch.batch_id
```
## Send Real-time Response commands to a single host
### Start a session
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
### Refresh the session to prevent expiration
**NOTE**: Required when you expect to exceed the default session expiration time (10 minutes).
```powershell
Update-FalconSession -SessionId $Session.session_id
```
## Use Real-time Response to upload and run an executable
**NOTE**: The command `Invoke-FalconDeploy` was developed to support mass-deployment of Falcon Forensics. It is designed to upload a file to your ‘Put’ Files library, create a session with target hosts, push the file to those hosts, then execute it and output the results to CSV.

**NOTE**: Because Real-time Response does not interact with logged in users, the executable must be able to be run silently and without user interaction.
```powershell
Invoke-FalconDeploy -HostIds <id>, <id> -Path $pwd\File.exe [-QueueOffline]
```
## Find Real-time Response sessions
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
## Manage Real-time Response scripts
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
## Manage Real-time Response ‘put’ files
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
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/90/real-time-response-apis)._