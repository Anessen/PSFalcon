![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
![Twitter URL](https://img.shields.io/twitter/url?label=Follow%20%40CrowdStrike&style=social&url=https%3A%2F%2Ftwitter.com%2FCrowdStrike)

_CrowdStrike API Documentation: [US-1](https://falcon.crowdstrike.com/support/documentation/201/sensor-update-policy-apis), [US-2](https://falcon.us-2.crowdstrike.com/support/documentation/201/sensor-update-policy-apis), [EU-1](https://falcon.eu-1.crowdstrike.com/support/documentation/201/sensor-update-policy-apis), [US-GOV-1](https://falcon.laggar.gcw.crowdstrike.com/support/documentation/201/sensor-update-policy-apis)._

|Command|Required Permission(s)|
|-------|----------------------|
|Copy-FalconDeviceControlPolicy|device-control-policies:read, device-control-policies:write|
|Copy-FalconFirewallPolicy|firewall-policies:read, firewall-policies:write|
|Copy-FalconPreventionPolicy|prevention-policies:read, prevention-policies:write|
|Copy-FalconResponsePolicy|response-policies:read, response-policies:write|
|Copy-FalconSensorUpdatePolicy|sensor-update-policies:read, sensor-update-policies:write|
|Edit-FalconSensorUpdatePolicy|sensor-update-policies:write|
|Get-FalconBuild|sensor-update-policies:read|
|Get-FalconKernel|sensor-update-policies:read|
|Get-FalconUninstallToken|sensor-update-policies:write|
|Get-FalconSensorUpdatePolicy|sensor-update-policies:read|
|Get-FalconSensorUpdatePolicyMember|sensor-update-policies:read|
|Invoke-FalconSensorUpdatePolicyAction|sensor-update-policies:write|
|New-FalconSensorUpdatePolicy|sensor-update-policies:write|
|Remove-FalconSensorUpdatePolicy|sensor-update-policies:write|
|Set-FalconSensorUpdatePrecedence|sensor-update-policies:write|

# Examples
## Determining available sensor versions for policy assignment
### Retrieve a list of available sensor versions
```powershell
Get-FalconBuild
```
### Retrieve a list of available Windows sensor versions
```powershell
Get-FalconBuild -Platform windows
```
## Retrieving kernel support information
### List results of a filtered search
```powershell
Get-FalconKernel -Filter "vendor:'ubuntu'+distro:'ubuntu20'+flavor:'gcp'+release:*'5.8.*'" -Sort vendor.asc
```
### Retrieve distro values
```powershell
Get-FalconKernel -Field distro -Sort vendor.asc
```
## Finding uninstallation tokens
### Finding a token for a host
```powershell
Get-FalconUninstallToken -DeviceId <id>
```
### Finding the maintenance token that applies to any host within a given policy
```powershell
Get-FalconUninstallToken -DeviceId MAINTENANCE
```
## Retrieve detailed Windows policies
```powershell
Get-FalconSensorUpdatePolicy -Filter "platform_name:'Windows'" -Detailed
```
## Manage Sensor Update policies
### Creating a policy
```powershell
New-FalconSensorUpdatePolicy -PlatformName Windows -Name 'My Windows Sensor Policy' -Settings @{ build = '14105|Auto'; uninstall_protection = 'ENABLED' } -Description 'Upgrades Windows hosts to latest sensor'
```
### Assigning host groups to a policy
```powershell
Invoke-FalconSensorUpdatePolicyAction -Name add-host-group -Id <id> -GroupId <id>
```
### Enabling a policy
```powershell
Invoke-FalconSensorUpdatePolicyAction -Name enable -Id <id>
```
### Set policy precedence
**NOTE**: All policy ids (with the exception of `platform_default`) must be supplied in precedence order.
```powershell
Set-FalconSensorUpdatePrecedence -PlatformName Windows -Ids <id1>, <id2>, <id3>, <id4>
```
### Delete a policy
```powershell
Remove-FalconSensorUpdatePolicy -Ids <id>, <id>
```