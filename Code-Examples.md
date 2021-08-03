***
**WARNING**: The code provided below is for example purposes only and is offered 'as is' with no support.
***
**NOTE**: These examples can be inserted into scripts, but are not designed to complete an entire workflow. _See [Basic Scripts](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts)._
## Authorization token request for a single CID
An example of how to include OAuth2 API Client information as parameters and perform an authorization token request. Once complete, the authorization token is stored within the PSFalcon module and re-used for subsequent requests.
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $ClientId,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{40}$')]
    [string] $ClientSecret,

    [Parameter()]
    [ValidateSet('us-1', 'us-2', 'us-gov-1', 'eu-1')]
    [string] $Cloud,

    [Parameter()]
    [ValidatePattern('^\w{32}$')]
    [string] $MemberCid
)
$Param = @{}
@('ClientId', 'ClientSecret', 'Cloud', 'MemberCid').foreach{
    if ($PSBoundParameters.$_) {
        $Param[$_] = $PSBoundParameters.$_
    }
}
Request-FalconToken @Param
```
## Retrieve a list of identifiers from a text file
To perform certain actions, you'll need an identifier for a specific resource within your Falcon environment--Host identifiers for Real-time Response or Network Containment, Host Group identifiers for policy assignment, etc.

The following example shows how you can add the retrieval of these identifiers, convert to an absolute file path, normalize the input (which sometimes is a problem when the values are converted to Json for an API request) and ignore any blank values. Once complete, you can use the `$Ids` variable with another PSFalcon command.
```powershell
#Requires -Version 5.1
param(
    [Parameter(Mandatory = $true)]
    [ValidateScript({
        if (Test-Path $_) {
            $true
        } else {
            throw "Cannot find path '$_' because it does not exist."
        }
    })]
    [string] $Path
)
$InputFile = if (![IO.Path]::IsPathRooted($PSBoundParameters.Path)) {
    $FullPath = Join-Path -Path (Get-Location).Path -ChildPath $PSBoundParameters.Path
    $FullPath = Join-Path -Path $FullPath -ChildPath '.'
    [IO.Path]::GetFullPath($FullPath)
} else {
    $PSBoundParameters.Path
}
$Ids = ((Get-Content -Path $InputFile).Normalize()).foreach{
    if ($_ -ne '') {
        $_
    }
}
```
***
**WARNING**: The code provided above is for example purposes only and is offered 'as is' with no support.
***