# Receive-FalconDiscoverAzureScript
## SYNOPSIS
Download a Bash script which grants Falcon Discover for Cloud access using Azure Cloud Shell
## DESCRIPTION
Requires 'D4C registration: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconDiscoverAzureScript [-Path] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-azure/entities/user-scripts-download/v1
```
### falconpy
[GetDiscoverCloudAzureUserScriptsAttachment](https://github.com/CrowdStrike/falconpy/wiki/d4c-registration#GetDiscoverCloudAzureUserScriptsAttachment)
## USAGE
### Enable Discover for Cloud and Containers with Azure provisioning script
```powershell
Receive-FalconDiscoverAzureScript -Path .\azure_provision.sh
```
_See [New-FalconDiscoverAzureAccount](New-FalconDiscoverAzureAccount)_.  ![Azure Provisioning Script Guide](https://img.shields.io/badge/Azure%20provisioning%20script%20guide-maroon?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAOCAYAAAAi2ky3AAABhWlDQ1BJQ0MgcHJvZmlsZQAAKJF9kT1Iw1AUhU9TpaIVBzuIOGSoDmJBVEQ3rUIRKoRaoVUHk5f+CE0akhQXR8G14ODPYtXBxVlXB1dBEPwBcXNzUnSREu9LCi1ifPB4H+e9c7jvXkColZhmtY0Cmm6bqURczGRXxNAruhAEMI1hmVnGrCQl4bu+7hHg512MZ/m/+3N1qzmLAQGReIYZpk28Tjy5aRuc94kjrCirxOfEIyYVSPzIdcXjN84FlwWeGTHTqTniCLFYaGGlhVnR1IgniKOqplO+kPFY5bzFWStVWKNO/sNwTl9e4jrtASSwgEVIEKGggg2UYCNGp06KhRTdx338/a5fIpdCrg0wcsyjDA2y6wefwe/eWvnxMS8pHAfaXxznYxAI7QL1quN8HztO/QQIPgNXetNfrgFTn6RXm1r0COjZBi6um5qyB1zuAH1PhmzKrsTnL+TzwPsZjSkL9N4Cnate3xr3OH0A0tSr5A1wcAgMFSh7zeffHa19+/dNo38/hq9yr+iELI0AAAAGYktHRAAAAAAAAPlDu38AAAAJcEhZcwAACxMAAAsTAQCanBgAAAAHdElNRQflDAsTByz7Va2cAAAAGXRFWHRDb21tZW50AENyZWF0ZWQgd2l0aCBHSU1QV4EOFwAAAYBJREFUKM+lkjFIlVEYht/zn3sFkYYUyUnIRcemhCtCU6JQOLiIU+QeJEQg6BBIm0s4RBCBLjq5OEvgJC1uOniJhivesLx17/97/vO9b4NK4g25157hfHCGB773/cA0HZIEAKiMj+LWiOxljG/i96pnCFP58XHnrWX2+9cj0dYl9Yu2FE9/9rXrcAAgs2eSyiBfOe/XRD503h/CuffOubQVUXL+Jh9BllzBbyJJBgDclVkO4Kukd8zzkXJbeUljIldFTstsmSHM6S81ma2KfPKlFdkGAMY4wzx/bbXapMy21My+YizdKNq5mDzLkrxafSxySFKjSWX2oTmjKzz4vN0r2lOFcL/Q3V0/mX95ILMXTTGYVfaut/aP2+oCMAvnZgCcsF5fcR0dg65YHAdwB+QApADvu0AuOe/ftlJAD7Nsgmm6yBjDtfWORJZlNtFyo/lR5Z7MyheKA5ktSur7sTAHazSG27pehjAiaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)[![EU 1](https://img.shields.io/badge/-EU--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.eu-1.crowdstrike.com/documentation/118/falcon-discover-for-cloud-and-containers-azure-subscription-apis#run-provisioning-script-in-azure-environment)[![US-1](https://img.shields.io/badge/-US--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.crowdstrike.com/documentation/118/falcon-discover-for-cloud-and-containers-azure-subscription-apis#run-provisioning-script-in-azure-environment)[![US-2](https://img.shields.io/badge/-US--2-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.us-2.crowdstrike.com/documentation/118/falcon-discover-for-cloud-and-containers-azure-subscription-apis#run-provisioning-script-in-azure-environment)[![US-GOV-1](https://img.shields.io/badge/-US--GOV--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.laggar.gcw.crowdstrike.com/documentation/118/falcon-discover-for-cloud-and-containers-azure-subscription-apis#run-provisioning-script-in-azure-environment)

_2023-04-25: PSFalcon v2.2.5_
