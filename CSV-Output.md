The `Export-FalconReport` command translates the API response into something that is more CSV friendly (including dropping certain fields due to redundancy or because they can't translate to a single column) and uses the PowerShell command `Export-Csv` to export it to CSV.

If one of these examples doesn't provide the specific data you're seeking, try using the PSFalcon command, manipulating the results, and using `Export-Csv` directly.

**NOTE**: Each of the following examples can be modified to filter for specific results or include additional parameters like `-All`.

## Custom IOCs

```powershell
Get-FalconIOC [-Detailed] [-All] | Export-FalconReport -Path .\IOCs.csv
```

## Custom Scripts and Put Files (Real-time Response)

```powershell
Get-FalconScript [-Detailed] [-All] | Export-FalconReport -Path .\Scripts.csv
```
```powershell
Get-FalconPutFile [-Detailed] [-All] | Export-FalconReport -Path .\PutFiles.csv
```

## Detections and Incidents

```powershell
Get-FalconDetection [-Detailed] [-All] | Export-FalconReport -Path .\Detections.csv
```
```powershell
Get-FalconIncident [-Detailed] [-All] | Export-FalconReport -Path .\Incidents.csv
```

## Hosts and Host Groups

```powershell
Get-FalconHost [-Detailed] [-All] | Export-FalconReport -Path .\Hosts.csv
```
```powershell
Get-FalconHostGroup [-Detailed] [-All] | Export-FalconReport -Path .\HostGroups.csv
```

## Policies

**NOTE**: Because settings vary between platforms, your output will be limited unless you filter for each Operating System.

```powershell
Get-FalconDeviceControlPolicy -Filter "platform_name:'Windows'" [-Detailed] [-All] | Export-FalconReport -Path .\DeviceControlPolicies.csv
```
```powershell
Get-FalconFirewallPolicy -Filter "platform_name:'Windows'" [-Detailed] [-All] | Export-FalconReport -Path .\FirewallPolicies.csv
```
```powershell
Get-FalconPreventionPolicy -Filter "platform_name:'Windows'" [-Detailed] [-All] | Export-FalconReport -Path .\PreventionPolicies.csv
```
```powershell
Get-FalconSensorUpdatePolicy -Filter "platform_name:'Windows'" [-Detailed] [-All] | Export-FalconReport -Path .\SensorUpdatePolicies.csv
```

## Users

```powershell
Get-FalconUser [-Detailed] [-All] | Export-FalconReport -Path .\Users.csv
```

## Vulnerabilities

```powershell
Get-FalconVulnerability [-Detailed] [-All] | Export-FalconReport -Path .\Vulnerabilities.csv
```