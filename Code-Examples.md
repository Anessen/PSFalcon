This page contains example code that can be used to help make scripts with PSFalcon.
## Authorization token request for a single CID
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