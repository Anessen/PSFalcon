***
**WARNING**: The code provided below is for example purposes only and is offered 'as is' with no support.
***
**NOTE**: These examples can be inserted into scripts, but are not designed to complete an entire workflow. _See [Basic Scripts](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts)._
## Authorization token request for a single CID
Include authorization information as parameters and perform a token request.
```powershell
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
***
**WARNING**: The code provided below is for example purposes only and is offered 'as is' with no support.
***