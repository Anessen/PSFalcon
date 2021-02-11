|cloud-connect-aws:read|cloud-connect-aws:write|
|-|-|
|Get-FalconDiscoverAwsAccount|Confirm-FalconDiscoverAwsAccess|
|Get-FalconDiscoverAwsSettings|Edit-FalconDiscoverAwsAccount|
||New-FalconDiscoverAwsAccount|
||Remove-FalconDiscoverAwsAccount|
||Update-FalconDiscoverAwsSettings|


|cspm-registration:read|cspm-registration:write|
|-|-|
|Get-FalconHorizonAwsAccount|Receive-FalconHorizonAzureScript|
|Get-FalconHorizonAwsLink|Edit-FalconHorizonAzureAccount|
|Get-FalconHorizonAzureAccount|Edit-FalconHorizonPolicy|
|Get-FalconHorizonPolicy|Edit-FalconHorizonSchedule|
|Get-FalconHorizonSchedule|New-FalconHorizonAwsAccount|
|Receive-FalconHorizonAwsScript|New-FalconHorizonAzureAccount|
||Remove-FalconHorizonAwsAccount|
||Remove-FalconHorizonAzureAccount|


|custom-ioa:read|custom-ioa:write|
|-|-|
|Get-FalconIOAGroup|Edit-FalconIOAGroup|
|Get-FalconIOAPlatform|Edit-FalconIOARule|
|Get-FalconIOARule|New-FalconIOAGroup|
|Get-FalconIOASeverity|New-FalconIOARule|
|Get-FalconIOAType|Remove-FalconIOAGroup|
||Remove-FalconIOARule|
||Test-FalconIOARule|


|d4c-registration:read|d4c-registration:write|
|-|-|
|Get-FalconDiscoverAzureAccount|New-FalconDiscoverAzureAccount|
|Get-FalconDiscoverGcpAccount|New-FalconDiscoverGcpAccount|
|Receive-FalconDiscoverGcpScript|Update-FalconDiscoverAzureAccount|


|detects:read|detects:write|
|-|-|
|Get-FalconDetection|Edit-FalconDetection|


|device-control-policies:read|device-control-policies:write|
|-|-|
|Get-FalconDeviceControlPolicy|Edit-FalconDeviceControlPolicy|
|Get-FalconDeviceControlPolicyMember|Invoke-FalconDeviceControlPolicyAction|
||New-FalconDeviceControlPolicy|
||Remove-FalconDeviceControlPolicy|
||Set-FalconDeviceControlPrecedence|


|devices:read|devices:write|
|-|-|
|Get-FalconHost|Add-FalconHostTag|
||Invoke-FalconHostAction|
||Remove-FalconHostTag|


|falconx-actors:read|
|-|
|Get-FalconActor|


|falconx-indicators:read|
|-|
|Get-FalconIndicator|


|falconx-reports:read|
|-|
|Get-FalconIntel|
|Receive-FalconIntel|


|falconx-rules:read|
|-|
|Get-FalconRule|
|Receive-FalconRule|


|falconx-sandbox:read|falconx-sandbox:write|
|-|-|
|Get-FalconReport|Get-FalconSample|
|Get-FalconSubmission|New-FalconSubmission|
|Receive-FalconArtifact|Remove-FalconReport|


|firewall-management:read|firewall-management:write|
|-|-|
|Get-FalconFirewallEvent|Edit-FalconFirewallGroup|
|Get-FalconFirewallField|Edit-FalconFirewallPolicy|
|Get-FalconFirewallGroup|Edit-FalconFirewallSetting|
|Get-FalconFirewallPlatform|Invoke-FalconFirewallPolicyAction|
|Get-FalconFirewallPolicy|New-FalconFirewallGroup|
|Get-FalconFirewallPolicyMember|New-FalconFirewallPolicy|
|Get-FalconFirewallRule|Remove-FalconFirewallGroup|
|Get-FalconFirewallSetting|Remove-FalconFirewallPolicy|
||Set-FalconFirewallPrecedence|


|host-group:read|host-group:write|
|-|-|
|Get-FalconHostGroup|Edit-FalconHostGroup|
|Get-FalconHostGroupMember|Invoke-FalconHostGroupAction|
||New-FalconHostGroup|
||Remove-FalconHostGroup|


|incidents:read|incidents:write|
|-|-|
|Get-FalconBehavior|Invoke-FalconIncidentAction|
|Get-FalconIncident||
|Get-FalconScore||


|installation-tokens:read|installation-tokens:write|
|-|-|
|Get-FalconInstallToken|Edit-FalconInstallToken|
|Get-FalconInstallTokenEvent|New-FalconInstallToken|
|Get-FalconInstallTokenSettings|Remove-FalconInstallToken|


|iocs:read|iocs:write|
|-|-|
|Get-FalconIOC|Edit-FalconIOC|
|Get-FalconIOCHost|New-FalconIOC|
|Get-FalconIOCProcess|Remove-FalconIOC|
|Get-FalconIOCTotal||
|Get-FalconProcess||


|malquery:read|malquery:write|
|-|-|
|Get-FalconMalQuery|Group-FalconMalQuerySample|
|Get-FalconMalQueryQuota|Invoke-FalconMalQuery|
|Get-FalconMalQuerySample|Search-FalconMalQueryHash|
|Receive-FalconMalQuerySample||


|ml-exclusions:read|ml-exclusions:write|
|-|-|
|Get-FalconMLExclusion|Edit-FalconMLExclusion|
||New-FalconMLExclusion|
||Remove-FalconMLExclusion|


|prevention-policies:read|prevention-policies:write|
|-|-|
|Get-FalconPreventionPolicy|Edit-FalconPreventionPolicy|
|Get-FalconPreventionPolicyMember|Invoke-FalconPreventionPolicyAction|
||New-FalconPreventionPolicy|
||Remove-FalconPreventionPolicy|
||Set-FalconPreventionPrecedence|


|quick-scan:read|quick-scan:write|
|-|-|
|Get-FalconQuickScan|New-FalconQuickScan|


|real-time-response:read|real-time-response:write|
|-|-|
|Confirm-FalconCommand|Confirm-FalconGetFile|
|Get-FalconSession|Confirm-FalconResponderCommand|
|Invoke-FalconCommand|Invoke-FalconBatchGet|
|Remove-FalconCommand|Invoke-FalconResponderCommand|
|Remove-FalconSession|Receive-FalconGetFile|
|Start-FalconSession|Remove-FalconGetFile|
|Update-FalconSession||


|real-time-response-admin:write|
|-|
|Confirm-FalconAdminCommand|
|Edit-FalconScript|
|Get-FalconPutFile|
|Get-FalconScript|
|Invoke-FalconAdminCommand|
|Remove-FalconPutFile|
|Remove-FalconScript|
|Send-FalconPutFile|
|Send-FalconScript|


|response-policies:read|response-policies:write|
|-|-|
|Get-FalconResponsePolicy|Invoke-FalconResponsePolicyAction|
|Get-FalconResponsePolicyMember|New-FalconResponsePolicy|
|Edit-FalconResponsePolicy|Remove-FalconResponsePolicy|
||Set-FalconResponsePrecedence|


|samplestore:read|samplestore:write|
|-|-|
|Receive-FalconSample|Remove-FalconSample|
||Send-FalconSample|


|self-service-ioa-exclusions:read|self-service-ioa-exclusions:write|
|-|-|
|Get-FalconIOAExclusion|Edit-FalconIOAExclusion|
||Remove-FalconIOAExclusion|


|sensor-installers:read|
|-|
|Get-FalconCCID|
|Get-FalconInstaller|
|Receive-FalconInstaller|


|sensor-update-policies:read|sensor-update-policies:write|
|-|-|
|Get-FalconBuild|Edit-FalconSensorUpdatePolicy|
|Get-FalconSensorUpdatePolicy|Get-FalconUninstallToken|
|Get-FalconSensorUpdatePolicyMember|Invoke-FalconSensorUpdatePolicyAction|
||New-FalconSensorUpdatePolicy|
||Remove-FalconSensorUpdatePolicy|
||Set-FalconSensorUpdatePrecedence|


|sensor-visibility-exclusions:read|sensor-visibility-exclusions:write|
|-|-|
|Get-FalconSVExclusion|Edit-FalconSVExclusion|
||New-FalconSVExclusion|
||Remove-FalconSVExclusion|


|spotlight-vulnerabilities:read|
|-|
|Get-FalconRemediation|
|Get-FalconVulnerability|


|streaming:read|
|-|
|Get-FalconStream|
|Open-FalconStream|
|Update-FalconStream|


|usermgmt:readusermgmt:read|usermgmt:write|
|-|-|
|Get-FalconRole|Add-FalconRole|
|Get-FalconUser|Edit-FalconUser|
||New-FalconUser|
||Remove-FalconRole|
||Remove-FalconUser|