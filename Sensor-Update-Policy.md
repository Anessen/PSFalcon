![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
![Twitter URL](https://img.shields.io/twitter/url?label=Follow%20%40CrowdStrike&style=social&url=https%3A%2F%2Ftwitter.com%2FCrowdStrike)

_CrowdStrike API Documentation: [US-1](https://falcon.crowdstrike.com/support/documentation/201/sensor-update-policy-apis), [US-2](https://falcon.us-2.crowdstrike.com/support/documentation/201/sensor-update-policy-apis), [EU-1](https://falcon.eu-1.crowdstrike.com/support/documentation/201/sensor-update-policy-apis), [US-GOV-1](https://falcon.laggar.gcw.crowdstrike.com/support/documentation/201/sensor-update-policy-apis)._

|Command|Required Permission(s)|
|-------|----------------------|
|Copy-FalconSensorUpdatePolicy|![sensor-update:read](https://img.shields.io/badge/Sensor%20Update-READ-red?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAOCAYAAAAi2ky3AAABhWlDQ1BJQ0MgcHJvZmlsZQAAKJF9kT1Iw1AUhU9TpaIVBzuIOGSoDmJBVEQ3rUIRKoRaoVUHk5f+CE0akhQXR8G14ODPYtXBxVlXB1dBEPwBcXNzUnSREu9LCi1ifPB4H+e9c7jvXkColZhmtY0Cmm6bqURczGRXxNAruhAEMI1hmVnGrCQl4bu+7hHg512MZ/m/+3N1qzmLAQGReIYZpk28Tjy5aRuc94kjrCirxOfEIyYVSPzIdcXjN84FlwWeGTHTqTniCLFYaGGlhVnR1IgniKOqplO+kPFY5bzFWStVWKNO/sNwTl9e4jrtASSwgEVIEKGggg2UYCNGp06KhRTdx338/a5fIpdCrg0wcsyjDA2y6wefwe/eWvnxMS8pHAfaXxznYxAI7QL1quN8HztO/QQIPgNXetNfrgFTn6RXm1r0COjZBi6um5qyB1zuAH1PhmzKrsTnL+TzwPsZjSkL9N4Cnate3xr3OH0A0tSr5A1wcAgMFSh7zeffHa19+/dNo38/hq9yr+iELI0AAAAGYktHRAAAAAAAAPlDu38AAAAJcEhZcwAACxMAAAsTAQCanBgAAAAHdElNRQflDAsTByz7Va2cAAAAGXRFWHRDb21tZW50AENyZWF0ZWQgd2l0aCBHSU1QV4EOFwAAAYBJREFUKM+lkjFIlVEYht/zn3sFkYYUyUnIRcemhCtCU6JQOLiIU+QeJEQg6BBIm0s4RBCBLjq5OEvgJC1uOniJhivesLx17/97/vO9b4NK4g25157hfHCGB773/cA0HZIEAKiMj+LWiOxljG/i96pnCFP58XHnrWX2+9cj0dYl9Yu2FE9/9rXrcAAgs2eSyiBfOe/XRD503h/CuffOubQVUXL+Jh9BllzBbyJJBgDclVkO4Kukd8zzkXJbeUljIldFTstsmSHM6S81ma2KfPKlFdkGAMY4wzx/bbXapMy21My+YizdKNq5mDzLkrxafSxySFKjSWX2oTmjKzz4vN0r2lOFcL/Q3V0/mX95ILMXTTGYVfaut/aP2+oCMAvnZgCcsF5fcR0dg65YHAdwB+QApADvu0AuOe/ftlJAD7Nsgmm6yBjDtfWORJZlNtFyo/lR5Z7MyheKA5ktSur7sTAHazSG27pehjAiaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)![sensor-update-policies:write](https://img.shields.io/badge/Sensor%20Update-WRITE-maroon?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAOCAYAAAAi2ky3AAABhWlDQ1BJQ0MgcHJvZmlsZQAAKJF9kT1Iw1AUhU9TpaIVBzuIOGSoDmJBVEQ3rUIRKoRaoVUHk5f+CE0akhQXR8G14ODPYtXBxVlXB1dBEPwBcXNzUnSREu9LCi1ifPB4H+e9c7jvXkColZhmtY0Cmm6bqURczGRXxNAruhAEMI1hmVnGrCQl4bu+7hHg512MZ/m/+3N1qzmLAQGReIYZpk28Tjy5aRuc94kjrCirxOfEIyYVSPzIdcXjN84FlwWeGTHTqTniCLFYaGGlhVnR1IgniKOqplO+kPFY5bzFWStVWKNO/sNwTl9e4jrtASSwgEVIEKGggg2UYCNGp06KhRTdx338/a5fIpdCrg0wcsyjDA2y6wefwe/eWvnxMS8pHAfaXxznYxAI7QL1quN8HztO/QQIPgNXetNfrgFTn6RXm1r0COjZBi6um5qyB1zuAH1PhmzKrsTnL+TzwPsZjSkL9N4Cnate3xr3OH0A0tSr5A1wcAgMFSh7zeffHa19+/dNo38/hq9yr+iELI0AAAAGYktHRAAAAAAAAPlDu38AAAAJcEhZcwAACxMAAAsTAQCanBgAAAAHdElNRQflDAsTByz7Va2cAAAAGXRFWHRDb21tZW50AENyZWF0ZWQgd2l0aCBHSU1QV4EOFwAAAYBJREFUKM+lkjFIlVEYht/zn3sFkYYUyUnIRcemhCtCU6JQOLiIU+QeJEQg6BBIm0s4RBCBLjq5OEvgJC1uOniJhivesLx17/97/vO9b4NK4g25157hfHCGB773/cA0HZIEAKiMj+LWiOxljG/i96pnCFP58XHnrWX2+9cj0dYl9Yu2FE9/9rXrcAAgs2eSyiBfOe/XRD503h/CuffOubQVUXL+Jh9BllzBbyJJBgDclVkO4Kukd8zzkXJbeUljIldFTstsmSHM6S81ma2KfPKlFdkGAMY4wzx/bbXapMy21My+YizdKNq5mDzLkrxafSxySFKjSWX2oTmjKzz4vN0r2lOFcL/Q3V0/mX95ILMXTTGYVfaut/aP2+oCMAvnZgCcsF5fcR0dg65YHAdwB+QApADvu0AuOe/ftlJAD7Nsgmm6yBjDtfWORJZlNtFyo/lR5Z7MyheKA5ktSur7sTAHazSG27pehjAiaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)|
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