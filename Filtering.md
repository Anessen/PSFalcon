![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
![API Documentation](https://img.shields.io/badge/API%20Documentation-maroon?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAOCAYAAAAi2ky3AAABhWlDQ1BJQ0MgcHJvZmlsZQAAKJF9kT1Iw1AUhU9TpaIVBzuIOGSoDmJBVEQ3rUIRKoRaoVUHk5f+CE0akhQXR8G14ODPYtXBxVlXB1dBEPwBcXNzUnSREu9LCi1ifPB4H+e9c7jvXkColZhmtY0Cmm6bqURczGRXxNAruhAEMI1hmVnGrCQl4bu+7hHg512MZ/m/+3N1qzmLAQGReIYZpk28Tjy5aRuc94kjrCirxOfEIyYVSPzIdcXjN84FlwWeGTHTqTniCLFYaGGlhVnR1IgniKOqplO+kPFY5bzFWStVWKNO/sNwTl9e4jrtASSwgEVIEKGggg2UYCNGp06KhRTdx338/a5fIpdCrg0wcsyjDA2y6wefwe/eWvnxMS8pHAfaXxznYxAI7QL1quN8HztO/QQIPgNXetNfrgFTn6RXm1r0COjZBi6um5qyB1zuAH1PhmzKrsTnL+TzwPsZjSkL9N4Cnate3xr3OH0A0tSr5A1wcAgMFSh7zeffHa19+/dNo38/hq9yr+iELI0AAAAGYktHRAAAAAAAAPlDu38AAAAJcEhZcwAACxMAAAsTAQCanBgAAAAHdElNRQflDAsTByz7Va2cAAAAGXRFWHRDb21tZW50AENyZWF0ZWQgd2l0aCBHSU1QV4EOFwAAAYBJREFUKM+lkjFIlVEYht/zn3sFkYYUyUnIRcemhCtCU6JQOLiIU+QeJEQg6BBIm0s4RBCBLjq5OEvgJC1uOniJhivesLx17/97/vO9b4NK4g25157hfHCGB773/cA0HZIEAKiMj+LWiOxljG/i96pnCFP58XHnrWX2+9cj0dYl9Yu2FE9/9rXrcAAgs2eSyiBfOe/XRD503h/CuffOubQVUXL+Jh9BllzBbyJJBgDclVkO4Kukd8zzkXJbeUljIldFTstsmSHM6S81ma2KfPKlFdkGAMY4wzx/bbXapMy21My+YizdKNq5mDzLkrxafSxySFKjSWX2oTmjKzz4vN0r2lOFcL/Q3V0/mX95ILMXTTGYVfaut/aP2+oCMAvnZgCcsF5fcR0dg65YHAdwB+QApADvu0AuOe/ftlJAD7Nsgmm6yBjDtfWORJZlNtFyo/lR5Z7MyheKA5ktSur7sTAHazSG27pehjAiaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)[![EU 1](https://img.shields.io/badge/-EU--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.eu-1.crowdstrike.com/support/documentation/45/falcon-query-language-fql)[![US-1](https://img.shields.io/badge/-US--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.crowdstrike.com/support/documentation/45/falcon-query-language-fql)[![US-2](https://img.shields.io/badge/-US--2-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.us-2.crowdstrike.com/support/documentation/45/falcon-query-language-fql)[![US-GOV-1](https://img.shields.io/badge/-US--GOV--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.laggar.gcw.crowdstrike.com/support/documentation/45/falcon-query-language-fql)

# Falcon Query Language
Many PSFalcon commands support the use of Falcon Query Language \("FQL"\) statements using the `-Filter` parameter. When using `-Filter`, it is important to keep in mind:

* **_Available FQL filters and their syntax will vary between APIs and are not determined by PSFalcon_**
* Each FQL filter and value may be case-sensitive (exact case, lowercase only, etc.)
* Each FQL filter statement can contain a maximum of 20 properties

Values in an FQL statement tend to either be restricted to `$true`, `$false`, an `integer` or a `string` (description, date or time, etc).

## Simple filters
The simplest FQL statements require a single condition and value. For instance, to find the host identifier for a device with the hostname `ONE`, use the following filter:
```powershell
Get-FalconHost -Filter "hostname:'ONE'"
```

Many filters will automatically return partial matches, but you can include wildcards \(`*`\):
```powershell
Get-FalconHost -Filter "hostname:*'*ONE*'"
```

Using square brackets will restrict results to exact matches \(including case\):
```powershell
Get-FalconHost -Filter "hostname:['ONE']"
```

## Multiple values
Additional conditions and values can be added using the proper operator. The following filter example will retrieve the host identifier for a device that has a hostname of `ONE` and is running Windows:
```powershell
Get-FalconHost -Filter "hostname:'ONE'+platform_name:'Windows'"
```

To find host identifiers for devices that are named `ONE` or `TWO`:
```powershell
Get-FalconHost -Filter "hostname:'ONE',hostname:'TWO'"
```

Multiple conditions can be used to retrieve more complex results. The following filter lists host identifiers for devices that are named `ONE` and are running Windows or are not named `TWO` and have been seen online within the last two days:
```powershell
Get-FalconHost -Filter "(hostname:'ONE'+platform_name:'Windows'),(hostname:!'TWO'+last_seen:>'Last 2 days')"
```

**NOTE**: 'Last 2 days' is not a valid FQL value when submitted via API. PSFalcon looks for a relative date string like `last <integer> hour(s)/day(s)` and automatically converts it into an RFC3339 \(UTC\) date string. For example, at exactly 14:00 hours \(Pacific Standard Time\) on November 10, 2020 if you attempted to use `Get-FalconHost` with the following filter, PSFalcon will convert your filter to the following value \(seen through the `Write-Verbose` output\).
```powershell
PS>Get-FalconHost -Filter "last_seen:>'Last 2 days'"
VERBOSE: [ApiClient.Invoke] ... ?filter=last_seen:>'2020-11-10T22:00:00Z'
```