***
**WARNING**: The code provided below is for example purposes only and is offered 'as is' with no support.
***
**NOTE**: These code snippets can be inserted into existing scripts to perform various tasks. 'Workflow' examples can be found under [Basic Scripts](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts).
## Authorization token request for a single CID
An example of how to include authorization information as parameters within a script.
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