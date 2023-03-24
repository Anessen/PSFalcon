![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
***
![API Documentation](https://img.shields.io/badge/API%20Documentation-maroon?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAOCAYAAAAi2ky3AAABhWlDQ1BJQ0MgcHJvZmlsZQAAKJF9kT1Iw1AUhU9TpaIVBzuIOGSoDmJBVEQ3rUIRKoRaoVUHk5f+CE0akhQXR8G14ODPYtXBxVlXB1dBEPwBcXNzUnSREu9LCi1ifPB4H+e9c7jvXkColZhmtY0Cmm6bqURczGRXxNAruhAEMI1hmVnGrCQl4bu+7hHg512MZ/m/+3N1qzmLAQGReIYZpk28Tjy5aRuc94kjrCirxOfEIyYVSPzIdcXjN84FlwWeGTHTqTniCLFYaGGlhVnR1IgniKOqplO+kPFY5bzFWStVWKNO/sNwTl9e4jrtASSwgEVIEKGggg2UYCNGp06KhRTdx338/a5fIpdCrg0wcsyjDA2y6wefwe/eWvnxMS8pHAfaXxznYxAI7QL1quN8HztO/QQIPgNXetNfrgFTn6RXm1r0COjZBi6um5qyB1zuAH1PhmzKrsTnL+TzwPsZjSkL9N4Cnate3xr3OH0A0tSr5A1wcAgMFSh7zeffHa19+/dNo38/hq9yr+iELI0AAAAGYktHRAAAAAAAAPlDu38AAAAJcEhZcwAACxMAAAsTAQCanBgAAAAHdElNRQflDAsTByz7Va2cAAAAGXRFWHRDb21tZW50AENyZWF0ZWQgd2l0aCBHSU1QV4EOFwAAAYBJREFUKM+lkjFIlVEYht/zn3sFkYYUyUnIRcemhCtCU6JQOLiIU+QeJEQg6BBIm0s4RBCBLjq5OEvgJC1uOniJhivesLx17/97/vO9b4NK4g25157hfHCGB773/cA0HZIEAKiMj+LWiOxljG/i96pnCFP58XHnrWX2+9cj0dYl9Yu2FE9/9rXrcAAgs2eSyiBfOe/XRD503h/CuffOubQVUXL+Jh9BllzBbyJJBgDclVkO4Kukd8zzkXJbeUljIldFTstsmSHM6S81ma2KfPKlFdkGAMY4wzx/bbXapMy21My+YizdKNq5mDzLkrxafSxySFKjSWX2oTmjKzz4vN0r2lOFcL/Q3V0/mX95ILMXTTGYVfaut/aP2+oCMAvnZgCcsF5fcR0dg65YHAdwB+QApADvu0AuOe/ftlJAD7Nsgmm6yBjDtfWORJZlNtFyo/lR5Z7MyheKA5ktSur7sTAHazSG27pehjAiaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)[![EU 1](https://img.shields.io/badge/-EU--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.eu-1.crowdstrike.com/support/documentation/45/falcon-query-language-fql)[![US-1](https://img.shields.io/badge/-US--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.crowdstrike.com/support/documentation/45/falcon-query-language-fql)[![US-2](https://img.shields.io/badge/-US--2-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.us-2.crowdstrike.com/support/documentation/45/falcon-query-language-fql)[![US-GOV-1](https://img.shields.io/badge/-US--GOV--1-grey?style=for-the-badge&labelColor=darkred&lo[%E2%80%A6]iaVfkN8b4XFIJ/wOzbOx07VNRUuHy7w98CzCcGPyWywAAAABJRU5ErkJggg==)](https://falcon.laggar.gcw.crowdstrike.com/support/documentation/45/falcon-query-language-fql)
- [Falcon Query Language](#falcon-query-language)
    - [Comparison operators](#comparison-operators)
    - [Multiple filters](#multiple-filters)
    - [Multiple values](#multiple-values)
    - [Timestamps](#timestamps)
***
# Falcon Query Language
Many PSFalcon commands support the use of Falcon Query Language \("FQL"\) statements using the `Filter`
parameter. When using `Filter`, it is important to keep in mind:

* **_Available FQL filters and their syntax will vary between APIs and are not determined by PSFalcon_**
* Each FQL filter and value may be case-sensitive (exact case, lowercase only, etc.)
* Each FQL filter statement can contain a maximum of 20 properties

Values in an FQL statement tend to either be restricted to `$true`, `$false`, `null`, an `integer`, or a `string`
(description, date or time, etc).

## Comparison operators
* `<`: Occurred before following value
* `>`: Occurred after following value
* `!`: Does not include following value
* `*`: Include following value as partial match
```powershell
-Filter "last_seen:>'YYYY-MM-DD'"
```
```powershell
-Filter "created_timestamp:<'YYYY-MM-DD'"
```
```powershell
-Filter "hostname:!'EXAMPLE-PC'"
```
```powershell
-Filter "name:*'*partial*'"
```
```powershell
-Filter "assigned_to_uid:null"
```
## Multiple filters
Multiple filters can be combined with `+` (AND) or `,` (OR). URL encoding is performed by PSFalcon automatically
when required.
```powershell
-Filter "expiration_on:>'2021-11-02'+last_execution.status:'DONE'"
```
## Multiple values
Multiple values for a single property must be enclosed within square brackets, with each `[string]` value being
enclosed in quotes.
```powershell
-Filter "name:['My','Example']"
```
## Timestamps
Timestamp filters use ISO 8601 format (`YYYY-MM-DDTHH:mm:ss.sssZ`). The timezone is always UTC (as denoted by "Z").

When entering a timestamp value, the full timestamp is not required. You can supply various full and partial date
and time combinations.

* Full date: `YYYY-MM-DD`
* Partial date: `YYYY-MM`, `YYYY`
* Full date with partial time: `YYYY-MM-DDThh`, `YYYY-MM-DDThh:mm`, `YYYY-MM-DDThh:mm:ss`
* Partial date with full time: `YYYY-MMthh:mm:ss.sZ`, `YYYYThh:mm:ss.sZ`
* Partial date with partial time: `YYYY-MM-Thh`, `YYYY-MM-Thh:mm`, `YYYY-MMThh:mm:ss`, `YYYYThh`, `YYYYThh:mm`, `YYYYThh:mm:ss`

**NOTE**: PSFalcon will automatically convert `last <int> days` and `last <int> hours` to a compatible UTC
timestamp.

Timestamps are expected when working with properties that display timestamps in result output. Timestamps will
often require comparison operators to match results.