[
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "QueryAWSAccounts",
        "path":  "/cloud-connect-aws/combined/accounts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Get-FalconDiscoverAwsAccount -Detailed"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "GetAWSSettings",
        "path":  "/cloud-connect-aws/combined/settings/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Get-FalconDiscoverAwsSetting"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "GetAWSAccounts",
        "path":  "/cloud-connect-aws/entities/accounts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Get-FalconDiscoverAwsAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "ProvisionAWSAccounts",
        "path":  "/cloud-connect-aws/entities/accounts/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "New-FalconDiscoverAwsAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "DeleteAWSAccounts",
        "path":  "/cloud-connect-aws/entities/accounts/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Remove-FalconDiscoverAwsAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "UpdateAWSAccounts",
        "path":  "/cloud-connect-aws/entities/accounts/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Edit-FalconDiscoverAwsAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "CreateOrUpdateAWSSettings",
        "path":  "/cloud-connect-aws/entities/settings/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Update-FalconDiscoverAwsSetting"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "VerifyAWSAccountAccess",
        "path":  "/cloud-connect-aws/entities/verify-account-access/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Confirm-FalconDiscoverAwsAccess -Id"
                     }
    },
    {
        "collection":  "cloud-connect-aws",
        "operationId":  "QueryAWSAccountsForIDs",
        "path":  "/cloud-connect-aws/queries/accounts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Get-FalconDiscoverAwsAccount"
                     }
    },
    {
        "collection":  "cloud-connect-azure",
        "operationId":  "GetCSPMAzureAccount",
        "path":  "/cloud-connect-azure/entities/account/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Get-FalconDiscoverAzureAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-azure",
        "operationId":  "CreateCSPMAzureAccount",
        "path":  "/cloud-connect-azure/entities/account/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "New-FalconDiscoverAzureAccount"
                     }
    },
    {
        "collection":  "cloud-connect-azure",
        "operationId":  "UpdateCSPMAzureAccountClientID",
        "path":  "/cloud-connect-azure/entities/client-id/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Update-FalconDiscoverAzureAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-azure",
        "operationId":  "GetCSPMAzureUserScriptsAttachment",
        "path":  "/cloud-connect-azure/entities/user-scripts-download/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Receive-FalconDiscoverAzureScript -Path"
                     }
    },
    {
        "collection":  "cloud-connect-azure",
        "operationId":  "GetCSPMAzureUserScripts",
        "path":  "/cloud-connect-azure/entities/user-scripts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "cloud-connect-cspm-aws",
        "operationId":  "GetCSPMAwsAccount",
        "path":  "/cloud-connect-cspm-aws/entities/account/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonAwsAccount"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-aws",
        "operationId":  "CreateCSPMAwsAccount",
        "path":  "/cloud-connect-cspm-aws/entities/account/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "New-FalconHorizonAwsAccount -AccountId"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-aws",
        "operationId":  "DeleteCSPMAwsAccount",
        "path":  "/cloud-connect-cspm-aws/entities/account/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Remove-FalconHorizonAwsAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-aws",
        "operationId":  "PatchCSPMAwsAccount",
        "path":  "/cloud-connect-cspm-aws/entities/account/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Edit-FalconHorizonAwsAccount -AccountId"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-aws",
        "operationId":  "GetCSPMAwsConsoleSetupURLs",
        "path":  "/cloud-connect-cspm-aws/entities/console-setup-urls/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonAwsLink"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-aws",
        "operationId":  "GetCSPMAwsAccountScriptsAttachment",
        "path":  "/cloud-connect-cspm-aws/entities/user-scripts-download/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Receive-FalconHorizonAwsScript -Path"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-azure",
        "operationId":  "GetCSPMAzureAccount",
        "path":  "/cloud-connect-cspm-azure/entities/account/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonAzureAccount"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-azure",
        "operationId":  "CreateCSPMAzureAccount",
        "path":  "/cloud-connect-cspm-azure/entities/account/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "New-FalconHorizonAzureAccount"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-azure",
        "operationId":  "DeleteCSPMAzureAccount",
        "path":  "/cloud-connect-cspm-azure/entities/account/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Remove-FalconHorizonAzureAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-azure",
        "operationId":  "UpdateCSPMAzureAccountClientID",
        "path":  "/cloud-connect-cspm-azure/entities/client-id/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Edit-FalconHorizonAzureAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-azure",
        "operationId":  "UpdateCSPMAzureTenantDefaultSubscriptionID",
        "path":  "/cloud-connect-cspm-azure/entities/default-subscription-id/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Edit-FalconHorizonAzureAccount -SubscriptionId"
                     }
    },
    {
        "collection":  "cloud-connect-cspm-azure",
        "operationId":  "GetCSPMAzureUserScriptsAttachment",
        "path":  "/cloud-connect-cspm-azure/entities/user-scripts-download/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Receive-FalconHorizonAzureScript -Path"
                     }
    },
    {
        "collection":  "cloud-connect-gcp",
        "operationId":  "GetCSPMCGPAccount",
        "path":  "/cloud-connect-gcp/entities/account/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Get-FalconDiscoverGcpAccount -Id"
                     }
    },
    {
        "collection":  "cloud-connect-gcp",
        "operationId":  "CreateCSPMGCPAccount",
        "path":  "/cloud-connect-gcp/entities/account/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "New-FalconDiscoverGcpAccount -ParentId"
                     }
    },
    {
        "collection":  "cloud-connect-gcp",
        "operationId":  "GetCSPMGCPUserScriptsAttachment",
        "path":  "/cloud-connect-gcp/entities/user-scripts-download/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover-for-Cloud-and-Containers",
                         "command":  "Receive-FalconDiscoverGcpScript -Path"
                     }
    },
    {
        "collection":  "cloud-connect-gcp",
        "operationId":  "GetCSPMGCPUserScripts",
        "path":  "/cloud-connect-gcp/entities/user-scripts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "container-security",
        "operationId":  "GetCredentials",
        "path":  "/container-security/entities/image-registry-credentials/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Get-FalconContainerToken"
                     }
    },
    {
        "collection":  "detects",
        "operationId":  "GetAggregateDetects",
        "path":  "/detects/aggregates/detects/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "detects",
        "operationId":  "UpdateDetectsByIdsV2",
        "path":  "/detects/entities/detects/v2",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Edit-FalconDetection -Id"
                     }
    },
    {
        "collection":  "detects",
        "operationId":  "GetBehaviorDetections",
        "path":  "/detects/entities/ioa/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonIoa"
                     }
    },
    {
        "collection":  "detects",
        "operationId":  "GetConfigurationDetections",
        "path":  "/detects/entities/iom/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonIom"
                     }
    },
    {
        "collection":  "detects",
        "operationId":  "GetDetectSummaries",
        "path":  "/detects/entities/summaries/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Get-FalconDetection -Id"
                     }
    },
    {
        "collection":  "detects",
        "operationId":  "QueryDetects",
        "path":  "/detects/queries/detects/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Get-FalconDetection"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "QueryDeviceLoginHistory",
        "path":  "/devices/combined/devices/login-history/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHost -Id -Login"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "QueryGetNetworkAddressHistoryV1",
        "path":  "/devices/combined/devices/network-address-history/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHost -Id -Network"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "queryCombinedGroupMembers",
        "path":  "/devices/combined/host-group-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHostGroupMember -Detailed"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "queryCombinedHostGroups",
        "path":  "/devices/combined/host-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHostGroup -Detailed"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "PerformActionV2",
        "path":  "/devices/entities/devices-actions/v2",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Invoke-FalconHostAction -Name -Id"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "UpdateDeviceTags",
        "path":  "/devices/entities/devices/tags/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Remove-FalconGroupingTag -Tag -Id"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "GetDeviceDetails",
        "path":  "/devices/entities/devices/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHost -Id"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "entities.perform_action",
        "path":  "/devices/entities/group-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "performGroupAction",
        "path":  "/devices/entities/host-group-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Invoke-FalconHostGroupAction -Name -Id -HostId"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "getHostGroups",
        "path":  "/devices/entities/host-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHostGroup -Id"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "createHostGroups",
        "path":  "/devices/entities/host-groups/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "New-FalconHostGroup -GroupType -Name"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "deleteHostGroups",
        "path":  "/devices/entities/host-groups/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Remove-FalconHostGroup -Id"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "updateHostGroups",
        "path":  "/devices/entities/host-groups/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Edit-FalconHostGroup -Id"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "GetOnlineState.V1",
        "path":  "/devices/entities/online-state/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHost -Id -State"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "QueryHiddenDevices",
        "path":  "/devices/queries/devices-hidden/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHost -Hidden"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "QueryDevicesByFilterScroll",
        "path":  "/devices/queries/devices-scroll/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHost"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "QueryDevicesByFilter",
        "path":  "/devices/queries/devices/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "queryGroupMembers",
        "path":  "/devices/queries/host-group-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHostGroupMember"
                     }
    },
    {
        "collection":  "devices",
        "operationId":  "queryHostGroups",
        "path":  "/devices/queries/host-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Get-FalconHostGroup"
                     }
    },
    {
        "collection":  "discover",
        "operationId":  "get-accounts",
        "path":  "/discover/entities/accounts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover",
                         "command":  "Get-FalconAsset -Id -Account"
                     }
    },
    {
        "collection":  "discover",
        "operationId":  "get-hosts",
        "path":  "/discover/entities/hosts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover",
                         "command":  "Get-FalconAsset -Id"
                     }
    },
    {
        "collection":  "discover",
        "operationId":  "get-logins",
        "path":  "/discover/entities/logins/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover",
                         "command":  "Get-FalconAsset -Id -Login"
                     }
    },
    {
        "collection":  "discover",
        "operationId":  "query-accounts",
        "path":  "/discover/queries/accounts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover",
                         "command":  "Get-FalconAsset -Account"
                     }
    },
    {
        "collection":  "discover",
        "operationId":  "query-hosts",
        "path":  "/discover/queries/hosts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover",
                         "command":  "Get-FalconAsset"
                     }
    },
    {
        "collection":  "discover",
        "operationId":  "query-logins",
        "path":  "/discover/queries/logins/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Discover",
                         "command":  "Get-FalconAsset -Login"
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "AggregateAllowList",
        "path":  "/falcon-complete-dashboards/aggregates/allowlist/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "AggregateBlockList",
        "path":  "/falcon-complete-dashboards/aggregates/blocklist/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "AggregateDetections",
        "path":  "/falcon-complete-dashboards/aggregates/detects/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "AggregateDeviceCountCollection",
        "path":  "/falcon-complete-dashboards/aggregates/devicecount-collections/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "AggregateEscalations",
        "path":  "/falcon-complete-dashboards/aggregates/escalations/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "AggregateFCIncidents",
        "path":  "/falcon-complete-dashboards/aggregates/incidents/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "AggregateRemediations",
        "path":  "/falcon-complete-dashboards/aggregates/remediations/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "QueryAllowListFilter",
        "path":  "/falcon-complete-dashboards/queries/allowlist/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Dashboards",
                         "command":  "Get-FalconCompleteAllowlist"
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "QueryBlockListFilter",
        "path":  "/falcon-complete-dashboards/queries/blocklist/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Dashboards",
                         "command":  "Get-FalconCompleteBlocklist"
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "QueryDetectionIdsByFilter",
        "path":  "/falcon-complete-dashboards/queries/detects/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Dashboards",
                         "command":  "Get-FalconCompleteDetection"
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "GetDeviceCountCollectionQueriesByFilter",
        "path":  "/falcon-complete-dashboards/queries/devicecount-collections/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Dashboards",
                         "command":  "Get-FalconCompleteCollection"
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "QueryEscalationsFilter",
        "path":  "/falcon-complete-dashboards/queries/escalations/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Dashboards",
                         "command":  "Get-FalconCompleteEscalation"
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "QueryIncidentIdsByFilter",
        "path":  "/falcon-complete-dashboards/queries/incidents/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Dashboards",
                         "command":  "Get-FalconCompleteIncident"
                     }
    },
    {
        "collection":  "falcon-complete-dashboards",
        "operationId":  "QueryRemediationsFilter",
        "path":  "/falcon-complete-dashboards/queries/remediations/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Dashboards",
                         "command":  "Get-FalconCompleteRemediation"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "GetArtifacts",
        "path":  "/falconx/entities/artifacts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Receive-FalconArtifact -Path -Id"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "GetSummaryReports",
        "path":  "/falconx/entities/report-summaries/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconReport -Id -Summary"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "GetReports",
        "path":  "/falconx/entities/reports/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconReport -Id"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "DeleteReport",
        "path":  "/falconx/entities/reports/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Remove-FalconReport -Id"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "GetSubmissions",
        "path":  "/falconx/entities/submissions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconSubmission -Id"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "Submit",
        "path":  "/falconx/entities/submissions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "New-FalconSubmission -EnvironmentId"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "QueryReports",
        "path":  "/falconx/queries/reports/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconReport"
                     }
    },
    {
        "collection":  "falconx",
        "operationId":  "QuerySubmissions",
        "path":  "/falconx/queries/submissions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconSubmissionQuota"
                     }
    },
    {
        "collection":  "filevantage",
        "operationId":  "getChanges",
        "path":  "/filevantage/entities/changes/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/FileVantage",
                         "command":  "Get-FalconFimChange -Id"
                     }
    },
    {
        "collection":  "filevantage",
        "operationId":  "queryChanges",
        "path":  "/filevantage/queries/changes/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/FileVantage",
                         "command":  "Get-FalconFimChange"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "aggregate-events",
        "path":  "/fwmgr/aggregates/events/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "aggregate-policy-rules",
        "path":  "/fwmgr/aggregates/policy-rules/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "aggregate-rule-groups",
        "path":  "/fwmgr/aggregates/rule-groups/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "aggregate-rules",
        "path":  "/fwmgr/aggregates/rules/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "get-events",
        "path":  "/fwmgr/entities/events/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallEvent -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "get-firewall-fields",
        "path":  "/fwmgr/entities/firewall-fields/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallField -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "get-platforms",
        "path":  "/fwmgr/entities/platforms/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallPlatform -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "get-policy-containers",
        "path":  "/fwmgr/entities/policies/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallSetting -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "update-policy-container",
        "path":  "/fwmgr/entities/policies/v1",
        "method":  "put",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Edit-FalconFirewallSetting -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "get-rule-groups",
        "path":  "/fwmgr/entities/rule-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallGroup -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "create-rule-group",
        "path":  "/fwmgr/entities/rule-groups/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "New-FalconFirewallGroup -Name -Enabled"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "delete-rule-groups",
        "path":  "/fwmgr/entities/rule-groups/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Remove-FalconFirewallGroup -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "update-rule-group",
        "path":  "/fwmgr/entities/rule-groups/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Edit-FalconFirewallGroup -DiffOperation -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "get-rules",
        "path":  "/fwmgr/entities/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallRule -Id"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "query-events",
        "path":  "/fwmgr/queries/events/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallEvent"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "query-firewall-fields",
        "path":  "/fwmgr/queries/firewall-fields/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallField"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "query-platforms",
        "path":  "/fwmgr/queries/platforms/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallPlatform"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "query-policy-rules",
        "path":  "/fwmgr/queries/policy-rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallRule -PolicyId"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "query-rule-groups",
        "path":  "/fwmgr/queries/rule-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallGroup"
                     }
    },
    {
        "collection":  "fwmgr",
        "operationId":  "query-rules",
        "path":  "/fwmgr/queries/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallRule"
                     }
    },
    {
        "collection":  "identity-protection",
        "operationId":  "api.preempt.proxy.post.graphql",
        "path":  "/identity-protection/combined/graphql/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "",
                         "command":  "Invoke-FalconIdentityGraph -Query"
                     }
    },
    {
        "collection":  "incidents",
        "operationId":  "CrowdScore",
        "path":  "/incidents/combined/crowdscores/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Get-FalconScore"
                     }
    },
    {
        "collection":  "incidents",
        "operationId":  "GetBehaviors",
        "path":  "/incidents/entities/behaviors/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Get-FalconBehavior -Id"
                     }
    },
    {
        "collection":  "incidents",
        "operationId":  "PerformIncidentAction",
        "path":  "/incidents/entities/incident-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Invoke-FalconIncidentAction -Name -Value -Id"
                     }
    },
    {
        "collection":  "incidents",
        "operationId":  "GetIncidents",
        "path":  "/incidents/entities/incidents/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Get-FalconIncident -Id"
                     }
    },
    {
        "collection":  "incidents",
        "operationId":  "QueryBehaviors",
        "path":  "/incidents/queries/behaviors/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Get-FalconBehavior"
                     }
    },
    {
        "collection":  "incidents",
        "operationId":  "QueryIncidents",
        "path":  "/incidents/queries/incidents/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Incident-and-Detection-Monitoring",
                         "command":  "Get-FalconIncident"
                     }
    },
    {
        "collection":  "indicators",
        "operationId":  "DevicesCount",
        "path":  "/indicators/aggregates/devices-count/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIocHost -Type -Value -Total"
                     }
    },
    {
        "collection":  "indicators",
        "operationId":  "DevicesRanOn",
        "path":  "/indicators/queries/devices/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIocHost -Type -Value"
                     }
    },
    {
        "collection":  "indicators",
        "operationId":  "ProcessesRanOn",
        "path":  "/indicators/queries/processes/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIocProcess -Type -Value -HostId"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "audit-events-read",
        "path":  "/installation-tokens/entities/audit-events/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "Get-FalconInstallTokenEvent -Id"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "customer-settings-read",
        "path":  "/installation-tokens/entities/customer-settings/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "Get-FalconInstallTokenSetting"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "tokens-read",
        "path":  "/installation-tokens/entities/tokens/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "Get-FalconInstallToken -Id"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "tokens-create",
        "path":  "/installation-tokens/entities/tokens/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "New-FalconInstallToken -Label -ExpiresTimestamp"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "tokens-delete",
        "path":  "/installation-tokens/entities/tokens/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "Remove-FalconInstallToken -Id"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "tokens-update",
        "path":  "/installation-tokens/entities/tokens/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "Edit-FalconInstallToken -Id"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "audit-events-query",
        "path":  "/installation-tokens/queries/audit-events/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "Get-FalconInstallTokenEvent"
                     }
    },
    {
        "collection":  "installation-tokens",
        "operationId":  "tokens-query",
        "path":  "/installation-tokens/queries/tokens/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Installation-Tokens",
                         "command":  "Get-FalconInstallToken"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "QueryIntelActorEntities",
        "path":  "/intel/combined/actors/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconActor -Detailed"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "QueryIntelIndicatorEntities",
        "path":  "/intel/combined/indicators/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconIndicator -Detailed"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "QueryIntelReportEntities",
        "path":  "/intel/combined/reports/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconIntel -Detailed"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "GetIntelActorEntities",
        "path":  "/intel/entities/actors/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconActor -Id"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "GetIntelIndicatorEntities",
        "path":  "/intel/entities/indicators/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconIndicator -Id"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "GetIntelReportPDF",
        "path":  "/intel/entities/report-files/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Receive-FalconIntel -Id"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "GetIntelReportEntities",
        "path":  "/intel/entities/reports/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconIntel -Id"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "GetIntelRuleFile",
        "path":  "/intel/entities/rules-files/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Receive-FalconRule -Path -Id"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "GetLatestIntelRuleFile",
        "path":  "/intel/entities/rules-latest-files/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Receive-FalconRule -Type -Path"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "GetIntelRuleEntities",
        "path":  "/intel/entities/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconRule -Id"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "QueryIntelActorIds",
        "path":  "/intel/queries/actors/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconActor"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "QueryIntelIndicatorIds",
        "path":  "/intel/queries/indicators/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconIndicator"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "QueryIntelReportIds",
        "path":  "/intel/queries/reports/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconIntel"
                     }
    },
    {
        "collection":  "intel",
        "operationId":  "QueryIntelRuleIds",
        "path":  "/intel/queries/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Intel",
                         "command":  "Get-FalconRule -Type"
                     }
    },
    {
        "collection":  "ioa",
        "operationId":  "GetIOAEvents",
        "path":  "/ioa/entities/events/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonIoaEvent -PolicyId"
                     }
    },
    {
        "collection":  "ioa",
        "operationId":  "GetIOAUsers",
        "path":  "/ioa/entities/users/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonIoaUser -PolicyId"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "get-patterns",
        "path":  "/ioarules/entities/pattern-severities/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaSeverity -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "get-platformsMixin0",
        "path":  "/ioarules/entities/platforms/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaPlatform -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "get-rule-groupsMixin0",
        "path":  "/ioarules/entities/rule-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaGroup -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "create-rule-groupMixin0",
        "path":  "/ioarules/entities/rule-groups/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "New-FalconIoaGroup -Name -Platform"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "delete-rule-groupsMixin0",
        "path":  "/ioarules/entities/rule-groups/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Remove-FalconIoaGroup -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "update-rule-groupMixin0",
        "path":  "/ioarules/entities/rule-groups/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Edit-FalconIoaGroup -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "get-rule-types",
        "path":  "/ioarules/entities/rule-types/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaType -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "get-rules-get",
        "path":  "/ioarules/entities/rules/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaRule -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "get-rulesMixin0",
        "path":  "/ioarules/entities/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "create-rule",
        "path":  "/ioarules/entities/rules/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "New-FalconIoaRule -Name -PatternSeverity -RuletypeId -DispositionId -FieldValue -RulegroupId"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "delete-rules",
        "path":  "/ioarules/entities/rules/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Remove-FalconIoaRule -RuleGroupId -Id"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "update-rules",
        "path":  "/ioarules/entities/rules/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Edit-FalconIoaRule -RulegroupId"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "validate",
        "path":  "/ioarules/entities/rules/validate/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Test-FalconIoaRule -Field"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "query-patterns",
        "path":  "/ioarules/queries/pattern-severities/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaSeverity"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "query-platformsMixin0",
        "path":  "/ioarules/queries/platforms/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaPlatform"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "query-rule-groups-full",
        "path":  "/ioarules/queries/rule-groups-full/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaGroup -Detailed"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "query-rule-groupsMixin0",
        "path":  "/ioarules/queries/rule-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaGroup"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "query-rule-types",
        "path":  "/ioarules/queries/rule-types/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaType"
                     }
    },
    {
        "collection":  "ioarules",
        "operationId":  "query-rulesMixin0",
        "path":  "/ioarules/queries/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaRule"
                     }
    },
    {
        "collection":  "iocs",
        "operationId":  "indicator.combined.v1",
        "path":  "/iocs/combined/indicator/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoc -Detailed"
                     }
    },
    {
        "collection":  "iocs",
        "operationId":  "indicator.get.v1",
        "path":  "/iocs/entities/indicators/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoc -Id"
                     }
    },
    {
        "collection":  "iocs",
        "operationId":  "indicator.create.v1",
        "path":  "/iocs/entities/indicators/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "New-FalconIoc -Action -Platform -Type -Value"
                     }
    },
    {
        "collection":  "iocs",
        "operationId":  "indicator.delete.v1",
        "path":  "/iocs/entities/indicators/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Remove-FalconIoc"
                     }
    },
    {
        "collection":  "iocs",
        "operationId":  "indicator.update.v1",
        "path":  "/iocs/entities/indicators/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Edit-FalconIoc -Id"
                     }
    },
    {
        "collection":  "iocs",
        "operationId":  "indicator.search.v1",
        "path":  "/iocs/queries/indicators/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoc"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "GetAWSAccountsMixin0",
        "path":  "/kubernetes-protection/entities/accounts/aws/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Get-FalconContainerAwsAccount"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "CreateAWSAccount",
        "path":  "/kubernetes-protection/entities/accounts/aws/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "New-FalconContainerAwsAccount -Region -Id"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "DeleteAWSAccountsMixin0",
        "path":  "/kubernetes-protection/entities/accounts/aws/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Remove-FalconContainerAwsAccount -Id"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "UpdateAWSAccount",
        "path":  "/kubernetes-protection/entities/accounts/aws/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Edit-FalconContainerAwsAccount -Id"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "GetLocations",
        "path":  "/kubernetes-protection/entities/cloud-locations/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Get-FalconContainerCloud"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "GetHelmValuesYaml",
        "path":  "/kubernetes-protection/entities/integration/agent/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Receive-FalconContainerYaml -Path -ClusterName"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "RegenerateAPIKey",
        "path":  "/kubernetes-protection/entities/integration/api-key/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "New-FalconContainerKey"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "GetClusters",
        "path":  "/kubernetes-protection/entities/kubernetes/clusters/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Get-FalconContainerCluster"
                     }
    },
    {
        "collection":  "kubernetes-protection",
        "operationId":  "TriggerScan",
        "path":  "/kubernetes-protection/entities/scan/trigger/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Kubernetes-Protection",
                         "command":  "Invoke-FalconContainerScan -ScanType"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "GetMalQueryQuotasV1",
        "path":  "/malquery/aggregates/quotas/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Get-FalconMalQueryQuota"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "PostMalQueryFuzzySearchV1",
        "path":  "/malquery/combined/fuzzy-search/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Invoke-FalconMalQuery -Type -Value -Fuzzy"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "GetMalQueryDownloadV1",
        "path":  "/malquery/entities/download-files/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Receive-FalconMalQuerySample -Path -Id"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "GetMalQueryMetadataV1",
        "path":  "/malquery/entities/metadata/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Get-FalconMalQuerySample -Id"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "GetMalQueryRequestV1",
        "path":  "/malquery/entities/requests/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Get-FalconMalQuery -Id"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "GetMalQueryEntitiesSamplesFetchV1",
        "path":  "/malquery/entities/samples-fetch/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "PostMalQueryEntitiesSamplesMultidownloadV1",
        "path":  "/malquery/entities/samples-multidownload/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Group-FalconMalQuerySample -Id"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "PostMalQueryExactSearchV1",
        "path":  "/malquery/queries/exact-search/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Invoke-FalconMalQuery -Type -Value"
                     }
    },
    {
        "collection":  "malquery",
        "operationId":  "PostMalQueryHuntV1",
        "path":  "/malquery/queries/hunt/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/MalQuery",
                         "command":  "Search-FalconMalQueryHash -Sha256"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "AggregateCases",
        "path":  "/message-center/aggregates/cases/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "GetCaseActivityByIds",
        "path":  "/message-center/entities/case-activities/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Get-FalconCompleteActivity -Id"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "CaseAddActivity",
        "path":  "/message-center/entities/case-activity/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Add-FalconCompleteActivity -Type -Content -UserId -Id"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "CaseDownloadAttachment",
        "path":  "/message-center/entities/case-attachment/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Receive-FalconCompleteAttachment -Path -Id"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "CaseAddAttachment",
        "path":  "/message-center/entities/case-attachment/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Send-FalconCompleteAttachment -Path -UserId -Id"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "CreateCase",
        "path":  "/message-center/entities/case/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "New-FalconCompleteCase -Type -Title -Content -UserId"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "UpdateCase",
        "path":  "/message-center/entities/case/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Edit-FalconCompleteCase -Id"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "GetCaseEntitiesByIDs",
        "path":  "/message-center/entities/cases/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Get-FalconCompleteCase -Id"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "QueryActivityByCaseID",
        "path":  "/message-center/queries/case-activities/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Get-FalconCompleteActivity -CaseId"
                     }
    },
    {
        "collection":  "message-center",
        "operationId":  "QueryCasesIdsByFilter",
        "path":  "/message-center/queries/cases/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-Complete-Message-Center",
                         "command":  "Get-FalconCompleteCase"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "getChildren",
        "path":  "/mssp/entities/children/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconMemberCid -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "getCIDGroupMembersBy",
        "path":  "/mssp/entities/cid-group-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconCidGroupMember -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "addCIDGroupMembers",
        "path":  "/mssp/entities/cid-group-members/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Add-FalconCidGroupMember -Id -Cid"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "deleteCIDGroupMembers",
        "path":  "/mssp/entities/cid-group-members/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Remove-FalconCidGroupMember -Id -Cid"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "getCIDGroupById",
        "path":  "/mssp/entities/cid-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconCidGroup -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "createCIDGroups",
        "path":  "/mssp/entities/cid-groups/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "New-FalconCidGroup -Name -Description"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "deleteCIDGroups",
        "path":  "/mssp/entities/cid-groups/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Remove-FalconCidGroup -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "updateCIDGroups",
        "path":  "/mssp/entities/cid-groups/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Edit-FalconCidGroup -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "getRolesByID",
        "path":  "/mssp/entities/mssp-roles/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconGroupRole -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "addRole",
        "path":  "/mssp/entities/mssp-roles/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Add-FalconGroupRole -CidGroupId -UserGroupId -RoleId"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "deletedRoles",
        "path":  "/mssp/entities/mssp-roles/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Remove-FalconGroupRole -CidGroupId -UserGroupId"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "getUserGroupMembersByID",
        "path":  "/mssp/entities/user-group-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconUserGroupMember -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "addUserGroupMembers",
        "path":  "/mssp/entities/user-group-members/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Add-FalconUserGroupMember -Id -UserId"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "deleteUserGroupMembers",
        "path":  "/mssp/entities/user-group-members/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Remove-FalconUserGroupMember -Id -UserId"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "getUserGroupsByID",
        "path":  "/mssp/entities/user-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconUserGroup -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "createUserGroups",
        "path":  "/mssp/entities/user-groups/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "New-FalconUserGroup -Name -Description"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "deleteUserGroups",
        "path":  "/mssp/entities/user-groups/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Remove-FalconUserGroup -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "updateUserGroups",
        "path":  "/mssp/entities/user-groups/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Edit-FalconUserGroup -Id"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "queryChildren",
        "path":  "/mssp/queries/children/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconMemberCid"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "queryCIDGroupMembers",
        "path":  "/mssp/queries/cid-group-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconCidGroupMember -Cid"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "queryCIDGroups",
        "path":  "/mssp/queries/cid-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconCidGroup"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "queryRoles",
        "path":  "/mssp/queries/mssp-roles/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconGroupRole"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "queryUserGroupMembers",
        "path":  "/mssp/queries/user-group-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconUserGroupMember -UserId"
                     }
    },
    {
        "collection":  "mssp",
        "operationId":  "queryUserGroups",
        "path":  "/mssp/queries/user-groups/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Flight-Control",
                         "command":  "Get-FalconUserGroup"
                     }
    },
    {
        "collection":  "oauth2",
        "operationId":  "oauth2RevokeToken",
        "path":  "/oauth2/revoke",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Authentication",
                         "command":  "Revoke-FalconToken"
                     }
    },
    {
        "collection":  "oauth2",
        "operationId":  "oauth2AccessToken",
        "path":  "/oauth2/token",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "overwatch-dashboards",
        "operationId":  "AggregatesDetectionsGlobalCounts",
        "path":  "/overwatch-dashboards/aggregates/detections-global-counts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-OverWatch-Dashboards",
                         "command":  "Get-FalconOverWatchDetection -Filter"
                     }
    },
    {
        "collection":  "overwatch-dashboards",
        "operationId":  "AggregatesEventsCollections",
        "path":  "/overwatch-dashboards/aggregates/events-collections/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "overwatch-dashboards",
        "operationId":  "AggregatesEvents",
        "path":  "/overwatch-dashboards/aggregates/events/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "overwatch-dashboards",
        "operationId":  "AggregatesIncidentsGlobalCounts",
        "path":  "/overwatch-dashboards/aggregates/incidents-global-counts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-OverWatch-Dashboards",
                         "command":  "Get-FalconOverWatchIncident -Filter"
                     }
    },
    {
        "collection":  "overwatch-dashboards",
        "operationId":  "AggregatesOWEventsGlobalCounts",
        "path":  "/overwatch-dashboards/aggregates/ow-events-global-counts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-OverWatch-Dashboards",
                         "command":  "Get-FalconOverWatchEvent -Filter"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedDeviceControlPolicyMembers",
        "path":  "/policy/combined/device-control-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Get-FalconDeviceControlPolicyMember -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedDeviceControlPolicies",
        "path":  "/policy/combined/device-control/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Get-FalconDeviceControlPolicy -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedFirewallPolicyMembers",
        "path":  "/policy/combined/firewall-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallPolicyMember -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedFirewallPolicies",
        "path":  "/policy/combined/firewall/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallPolicy -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedPreventionPolicyMembers",
        "path":  "/policy/combined/prevention-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconPreventionPolicyMember -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedPreventionPolicies",
        "path":  "/policy/combined/prevention/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconPreventionPolicy -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedRTResponsePolicyMembers",
        "path":  "/policy/combined/response-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Get-FalconResponsePolicyMember -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedRTResponsePolicies",
        "path":  "/policy/combined/response/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Get-FalconResponsePolicy -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "revealUninstallToken",
        "path":  "/policy/combined/reveal-uninstall-token/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Host-and-Host-Group-Management",
                         "command":  "Uninstall-FalconSensor -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedSensorUpdateBuilds",
        "path":  "/policy/combined/sensor-update-builds/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Get-FalconBuild"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedSensorUpdateKernels",
        "path":  "/policy/combined/sensor-update-kernels/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Get-FalconKernel"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedSensorUpdatePolicyMembers",
        "path":  "/policy/combined/sensor-update-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Get-FalconSensorUpdatePolicyMember -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedSensorUpdatePolicies",
        "path":  "/policy/combined/sensor-update/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryCombinedSensorUpdatePoliciesV2",
        "path":  "/policy/combined/sensor-update/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Get-FalconSensorUpdatePolicy -Detailed"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "performDeviceControlPoliciesAction",
        "path":  "/policy/entities/device-control-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Invoke-FalconDeviceControlPolicyAction -Name -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "setDeviceControlPoliciesPrecedence",
        "path":  "/policy/entities/device-control-precedence/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Set-FalconDeviceControlPrecedence -PlatformName -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getDeviceControlPolicies",
        "path":  "/policy/entities/device-control/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Get-FalconDeviceControlPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createDeviceControlPolicies",
        "path":  "/policy/entities/device-control/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "New-FalconDeviceControlPolicy -Name -PlatformName"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deleteDeviceControlPolicies",
        "path":  "/policy/entities/device-control/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Remove-FalconDeviceControlPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateDeviceControlPolicies",
        "path":  "/policy/entities/device-control/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Edit-FalconDeviceControlPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "performFirewallPoliciesAction",
        "path":  "/policy/entities/firewall-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Invoke-FalconFirewallPolicyAction -Name -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "setFirewallPoliciesPrecedence",
        "path":  "/policy/entities/firewall-precedence/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Set-FalconFirewallPrecedence -PlatformName -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getFirewallPolicies",
        "path":  "/policy/entities/firewall/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createFirewallPolicies",
        "path":  "/policy/entities/firewall/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "New-FalconFirewallPolicy -Name -PlatformName"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deleteFirewallPolicies",
        "path":  "/policy/entities/firewall/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Remove-FalconFirewallPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateFirewallPolicies",
        "path":  "/policy/entities/firewall/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Edit-FalconFirewallPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getIOAExclusionsV1",
        "path":  "/policy/entities/ioa-exclusions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createIOAExclusionsV1",
        "path":  "/policy/entities/ioa-exclusions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "New-FalconIoaExclusion -Name -PatternId -PatternName -ClRegex -IfnRegex"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deleteIOAExclusionsV1",
        "path":  "/policy/entities/ioa-exclusions/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Remove-FalconIoaExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateIOAExclusionsV1",
        "path":  "/policy/entities/ioa-exclusions/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Edit-FalconIoaExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getMLExclusionsV1",
        "path":  "/policy/entities/ml-exclusions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconMlExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createMLExclusionsV1",
        "path":  "/policy/entities/ml-exclusions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "New-FalconMlExclusion -Value -ExcludedFrom -GroupId"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deleteMLExclusionsV1",
        "path":  "/policy/entities/ml-exclusions/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Remove-FalconMlExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateMLExclusionsV1",
        "path":  "/policy/entities/ml-exclusions/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Edit-FalconMlExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "performPreventionPoliciesAction",
        "path":  "/policy/entities/prevention-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Invoke-FalconPreventionPolicyAction -Name -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "setPreventionPoliciesPrecedence",
        "path":  "/policy/entities/prevention-precedence/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Set-FalconPreventionPrecedence -PlatformName -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getPreventionPolicies",
        "path":  "/policy/entities/prevention/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconPreventionPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createPreventionPolicies",
        "path":  "/policy/entities/prevention/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "New-FalconPreventionPolicy -Name -PlatformName"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deletePreventionPolicies",
        "path":  "/policy/entities/prevention/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Remove-FalconPreventionPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updatePreventionPolicies",
        "path":  "/policy/entities/prevention/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Edit-FalconPreventionPolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "performRTResponsePoliciesAction",
        "path":  "/policy/entities/response-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Invoke-FalconResponsePolicyAction -Name -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "setRTResponsePoliciesPrecedence",
        "path":  "/policy/entities/response-precedence/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Set-FalconResponsePrecedence -PlatformName -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getRTResponsePolicies",
        "path":  "/policy/entities/response/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Get-FalconResponsePolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createRTResponsePolicies",
        "path":  "/policy/entities/response/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "New-FalconResponsePolicy -Name -PlatformName"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deleteRTResponsePolicies",
        "path":  "/policy/entities/response/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Remove-FalconResponsePolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateRTResponsePolicies",
        "path":  "/policy/entities/response/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Edit-FalconResponsePolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "performSensorUpdatePoliciesAction",
        "path":  "/policy/entities/sensor-update-actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Invoke-FalconSensorUpdatePolicyAction -Name -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "setSensorUpdatePoliciesPrecedence",
        "path":  "/policy/entities/sensor-update-precedence/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Set-FalconSensorUpdatePrecedence -PlatformName -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getSensorUpdatePolicies",
        "path":  "/policy/entities/sensor-update/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createSensorUpdatePolicies",
        "path":  "/policy/entities/sensor-update/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deleteSensorUpdatePolicies",
        "path":  "/policy/entities/sensor-update/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Remove-FalconSensorUpdatePolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateSensorUpdatePolicies",
        "path":  "/policy/entities/sensor-update/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getSensorUpdatePoliciesV2",
        "path":  "/policy/entities/sensor-update/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Get-FalconSensorUpdatePolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createSensorUpdatePoliciesV2",
        "path":  "/policy/entities/sensor-update/v2",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "New-FalconSensorUpdatePolicy -Name -PlatformName"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateSensorUpdatePoliciesV2",
        "path":  "/policy/entities/sensor-update/v2",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Edit-FalconSensorUpdatePolicy -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "getSensorVisibilityExclusionsV1",
        "path":  "/policy/entities/sv-exclusions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconSvExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "createSVExclusionsV1",
        "path":  "/policy/entities/sv-exclusions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "New-FalconSvExclusion -Value -GroupId"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "deleteSensorVisibilityExclusionsV1",
        "path":  "/policy/entities/sv-exclusions/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Remove-FalconSvExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "updateSensorVisibilityExclusionsV1",
        "path":  "/policy/entities/sv-exclusions/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Edit-FalconSvExclusion -Id"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryDeviceControlPolicyMembers",
        "path":  "/policy/queries/device-control-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Get-FalconDeviceControlPolicyMember"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryDeviceControlPolicies",
        "path":  "/policy/queries/device-control/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/USB-Device-Control-Policy",
                         "command":  "Get-FalconDeviceControlPolicy"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryFirewallPolicyMembers",
        "path":  "/policy/queries/firewall-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallPolicyMember"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryFirewallPolicies",
        "path":  "/policy/queries/firewall/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Firewall-Management",
                         "command":  "Get-FalconFirewallPolicy"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryIOAExclusionsV1",
        "path":  "/policy/queries/ioa-exclusions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIoaExclusion"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryMLExclusionsV1",
        "path":  "/policy/queries/ml-exclusions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconMlExclusion"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryPreventionPolicyMembers",
        "path":  "/policy/queries/prevention-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconPreventionPolicyMember"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryPreventionPolicies",
        "path":  "/policy/queries/prevention/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconPreventionPolicy"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryRTResponsePolicyMembers",
        "path":  "/policy/queries/response-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Get-FalconResponsePolicyMember"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "queryRTResponsePolicies",
        "path":  "/policy/queries/response/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response-Policy",
                         "command":  "Get-FalconResponsePolicy"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "querySensorUpdateKernelsDistinct",
        "path":  "/policy/queries/sensor-update-kernels/{distinct-field}/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "querySensorUpdatePolicyMembers",
        "path":  "/policy/queries/sensor-update-members/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Get-FalconSensorUpdatePolicyMember"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "querySensorUpdatePolicies",
        "path":  "/policy/queries/sensor-update/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Update-Policy",
                         "command":  "Get-FalconSensorUpdatePolicy"
                     }
    },
    {
        "collection":  "policy",
        "operationId":  "querySensorVisibilityExclusionsV1",
        "path":  "/policy/queries/sv-exclusions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconSvExclusion"
                     }
    },
    {
        "collection":  "processes",
        "operationId":  "entities.processes",
        "path":  "/processes/entities/processes/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Detection-and-Prevention-Policies",
                         "command":  "Get-FalconIocProcess -Id"
                     }
    },
    {
        "collection":  "quarantine",
        "operationId":  "ActionUpdateCount",
        "path":  "/quarantine/aggregates/action-update-count/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Quarantine",
                         "command":  "Test-FalconQuarantineAction -Filter"
                     }
    },
    {
        "collection":  "quarantine",
        "operationId":  "GetAggregateFiles",
        "path":  "/quarantine/aggregates/quarantined-files/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "quarantine",
        "operationId":  "GetQuarantineFiles",
        "path":  "/quarantine/entities/quarantined-files/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Quarantine",
                         "command":  "Get-FalconQuarantine -Id"
                     }
    },
    {
        "collection":  "quarantine",
        "operationId":  "UpdateQuarantinedDetectsByIds",
        "path":  "/quarantine/entities/quarantined-files/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Quarantine",
                         "command":  "Invoke-FalconQuarantineAction -Action -Id"
                     }
    },
    {
        "collection":  "quarantine",
        "operationId":  "QueryQuarantineFiles",
        "path":  "/quarantine/queries/quarantined-files/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Quarantine",
                         "command":  "Get-FalconQuarantine"
                     }
    },
    {
        "collection":  "quarantine",
        "operationId":  "UpdateQfByQuery",
        "path":  "/quarantine/queries/quarantined-files/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/CrowdStrike/psfalcon/wiki/Quarantine",
                         "command":  "Invoke-FalconQuarantineAction -Action -Filter"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-AggregateSessions",
        "path":  "/real-time-response/aggregates/sessions/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "BatchActiveResponderCmd",
        "path":  "/real-time-response/combined/batch-active-responder-command/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Invoke-FalconResponderCommand -Command -BatchId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "BatchAdminCmd",
        "path":  "/real-time-response/combined/batch-admin-command/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Invoke-FalconAdminCommand -Command -BatchId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "BatchCmd",
        "path":  "/real-time-response/combined/batch-command/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Invoke-FalconCommand -Command -BatchId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "BatchGetCmdStatus",
        "path":  "/real-time-response/combined/batch-get-command/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Confirm-FalconGetFile -BatchGetCmdReqId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "BatchGetCmd",
        "path":  "/real-time-response/combined/batch-get-command/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Invoke-FalconBatchGet -FilePath -BatchId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "BatchInitSessions",
        "path":  "/real-time-response/combined/batch-init-session/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Start-FalconSession -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "BatchRefreshSessions",
        "path":  "/real-time-response/combined/batch-refresh-session/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Update-FalconSession -BatchId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-CheckActiveResponderCommandStatus",
        "path":  "/real-time-response/entities/active-responder-command/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Confirm-FalconResponderCommand -CloudRequestId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ExecuteActiveResponderCommand",
        "path":  "/real-time-response/entities/active-responder-command/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Invoke-FalconResponderCommand -Command -SessionId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-CheckAdminCommandStatus",
        "path":  "/real-time-response/entities/admin-command/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Confirm-FalconAdminCommand -CloudRequestId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ExecuteAdminCommand",
        "path":  "/real-time-response/entities/admin-command/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Invoke-FalconAdminCommand -Command -SessionId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-CheckCommandStatus",
        "path":  "/real-time-response/entities/command/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Confirm-FalconCommand -CloudRequestId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ExecuteCommand",
        "path":  "/real-time-response/entities/command/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Invoke-FalconCommand -Command -SessionId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-GetExtractedFileContents",
        "path":  "/real-time-response/entities/extracted-file-contents/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Receive-FalconGetFile -Sha256 -SessionId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ListFiles",
        "path":  "/real-time-response/entities/file/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-DeleteFile",
        "path":  "/real-time-response/entities/file/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ListFilesV2",
        "path":  "/real-time-response/entities/file/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Confirm-FalconGetFile -SessionId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-DeleteFileV2",
        "path":  "/real-time-response/entities/file/v2",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Remove-FalconGetFile -SessionId -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-GetPut-Files",
        "path":  "/real-time-response/entities/put-files/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Get-FalconPutFile -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-CreatePut-Files",
        "path":  "/real-time-response/entities/put-files/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Send-FalconPutFile -Path"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-DeletePut-Files",
        "path":  "/real-time-response/entities/put-files/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Remove-FalconPutFile -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ListQueuedSessions",
        "path":  "/real-time-response/entities/queued-sessions/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Get-FalconSession -Id -Queue"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-DeleteQueuedSession",
        "path":  "/real-time-response/entities/queued-sessions/command/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Remove-FalconCommand -SessionId -CloudRequestId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-PulseSession",
        "path":  "/real-time-response/entities/refresh-session/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Update-FalconSession -HostId"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-GetScripts",
        "path":  "/real-time-response/entities/scripts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Get-FalconScript -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-CreateScripts",
        "path":  "/real-time-response/entities/scripts/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Send-FalconScript -Platform -PermissionType -Path"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-DeleteScripts",
        "path":  "/real-time-response/entities/scripts/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Remove-FalconScript -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-UpdateScripts",
        "path":  "/real-time-response/entities/scripts/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Edit-FalconScript -Path -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ListSessions",
        "path":  "/real-time-response/entities/sessions/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Get-FalconSession -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-InitSession",
        "path":  "/real-time-response/entities/sessions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Start-FalconSession -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-DeleteSession",
        "path":  "/real-time-response/entities/sessions/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Remove-FalconSession -Id"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ListPut-Files",
        "path":  "/real-time-response/queries/put-files/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Get-FalconPutFile"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ListScripts",
        "path":  "/real-time-response/queries/scripts/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Get-FalconScript"
                     }
    },
    {
        "collection":  "real-time-response",
        "operationId":  "RTR-ListAllSessions",
        "path":  "/real-time-response/queries/sessions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Real-time-Response",
                         "command":  "Get-FalconSession"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "AggregateNotificationsV1",
        "path":  "/recon/aggregates/notifications/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "PreviewRuleV1",
        "path":  "/recon/aggregates/rules-preview/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconRulePreview -Topic -Filter"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "GetActionsV1",
        "path":  "/recon/entities/actions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconAction -Id"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "CreateActionsV1",
        "path":  "/recon/entities/actions/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "New-FalconReconAction -RuleId -Type -Frequency -Recipient"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "DeleteActionV1",
        "path":  "/recon/entities/actions/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Remove-FalconReconAction -Id"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "UpdateActionV1",
        "path":  "/recon/entities/actions/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Edit-FalconReconAction -Frequency -Recipient -Status -Id"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "GetNotificationsDetailedTranslatedV1",
        "path":  "/recon/entities/notifications-detailed-translated/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconNotification -Id -Combined"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "GetNotificationsDetailedV1",
        "path":  "/recon/entities/notifications-detailed/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconNotification -Id -Intel"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "GetNotificationsTranslatedV1",
        "path":  "/recon/entities/notifications-translated/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconNotification -Id -Translate"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "GetNotificationsV1",
        "path":  "/recon/entities/notifications/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconNotification -Id"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "DeleteNotificationsV1",
        "path":  "/recon/entities/notifications/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Remove-FalconReconNotification -Id"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "UpdateNotificationsV1",
        "path":  "/recon/entities/notifications/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Edit-FalconReconNotification -Id -Status -AssignedToUuid"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "GetRulesV1",
        "path":  "/recon/entities/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconRule -Id"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "CreateRulesV1",
        "path":  "/recon/entities/rules/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "New-FalconReconRule -Name -Topic -Filter -Priority -Permission"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "DeleteRulesV1",
        "path":  "/recon/entities/rules/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Remove-FalconReconRule -Id"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "UpdateRulesV1",
        "path":  "/recon/entities/rules/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Edit-FalconReconRule -Id -Name -Filter -Priority -Permission"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "QueryActionsV1",
        "path":  "/recon/queries/actions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconAction"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "QueryNotificationsV1",
        "path":  "/recon/queries/notifications/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconNotification"
                     }
    },
    {
        "collection":  "recon",
        "operationId":  "QueryRulesV1",
        "path":  "/recon/queries/rules/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X-Recon",
                         "command":  "Get-FalconReconRule"
                     }
    },
    {
        "collection":  "reports",
        "operationId":  "report-executions-download.get",
        "path":  "/reports/entities/report-executions-download/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Scheduled-Reports-and-Searches",
                         "command":  "Receive-FalconScheduledReport -Id"
                     }
    },
    {
        "collection":  "reports",
        "operationId":  "report-executions.retry",
        "path":  "/reports/entities/report-executions-retry/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Scheduled-Reports-and-Searches",
                         "command":  "Redo-FalconScheduledReport -Id"
                     }
    },
    {
        "collection":  "reports",
        "operationId":  "report-executions.get",
        "path":  "/reports/entities/report-executions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Scheduled-Reports-and-Searches",
                         "command":  "Get-FalconScheduledReport -Id -Execution"
                     }
    },
    {
        "collection":  "reports",
        "operationId":  "scheduled-reports.launch",
        "path":  "/reports/entities/scheduled-reports/execution/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Scheduled-Reports-and-Searches",
                         "command":  "Invoke-FalconScheduledReport -Id"
                     }
    },
    {
        "collection":  "reports",
        "operationId":  "scheduled-reports.get",
        "path":  "/reports/entities/scheduled-reports/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Scheduled-Reports-and-Searches",
                         "command":  "Get-FalconScheduledReport -Id"
                     }
    },
    {
        "collection":  "reports",
        "operationId":  "report-executions.query",
        "path":  "/reports/queries/report-executions/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Scheduled-Reports-and-Searches",
                         "command":  "Get-FalconScheduledReport -Execution"
                     }
    },
    {
        "collection":  "reports",
        "operationId":  "scheduled-reports.query",
        "path":  "/reports/queries/scheduled-reports/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Scheduled-Reports-and-Searches",
                         "command":  "Get-FalconScheduledReport"
                     }
    },
    {
        "collection":  "samples",
        "operationId":  "GetSampleV2",
        "path":  "/samples/entities/samples/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "samples",
        "operationId":  "UploadSampleV2",
        "path":  "/samples/entities/samples/v2",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "samples",
        "operationId":  "DeleteSampleV2",
        "path":  "/samples/entities/samples/v2",
        "method":  "delete",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "samples",
        "operationId":  "GetSampleV3",
        "path":  "/samples/entities/samples/v3",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Receive-FalconSample -Path -Id"
                     }
    },
    {
        "collection":  "samples",
        "operationId":  "UploadSampleV3",
        "path":  "/samples/entities/samples/v3",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Send-FalconSample -Path"
                     }
    },
    {
        "collection":  "samples",
        "operationId":  "DeleteSampleV3",
        "path":  "/samples/entities/samples/v3",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Remove-FalconSample -Id"
                     }
    },
    {
        "collection":  "samples",
        "operationId":  "QuerySampleV1",
        "path":  "/samples/queries/samples/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconSample -Id"
                     }
    },
    {
        "collection":  "scanner",
        "operationId":  "GetScansAggregates",
        "path":  "/scanner/aggregates/scans/GET/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "scanner",
        "operationId":  "GetScans",
        "path":  "/scanner/entities/scans/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconQuickScan -Id"
                     }
    },
    {
        "collection":  "scanner",
        "operationId":  "ScanSamples",
        "path":  "/scanner/entities/scans/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "New-FalconQuickScan -Id"
                     }
    },
    {
        "collection":  "scanner",
        "operationId":  "QuerySubmissionsMixin0",
        "path":  "/scanner/queries/scans/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Falcon-X",
                         "command":  "Get-FalconQuickScanQuota"
                     }
    },
    {
        "collection":  "sensors",
        "operationId":  "GetCombinedSensorInstallersByQuery",
        "path":  "/sensors/combined/installers/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Download",
                         "command":  "Get-FalconInstaller -Detailed"
                     }
    },
    {
        "collection":  "sensors",
        "operationId":  "refreshActiveStreamSession",
        "path":  "/sensors/entities/datafeed-actions/v1/{partition}",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Event-Streams",
                         "command":  "Update-FalconStream -AppId -Partition"
                     }
    },
    {
        "collection":  "sensors",
        "operationId":  "listAvailableStreamsOAuth2",
        "path":  "/sensors/entities/datafeed/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Event-Streams",
                         "command":  "Get-FalconStream -AppId"
                     }
    },
    {
        "collection":  "sensors",
        "operationId":  "DownloadSensorInstallerById",
        "path":  "/sensors/entities/download-installer/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Download",
                         "command":  "Receive-FalconInstaller -Path -Id"
                     }
    },
    {
        "collection":  "sensors",
        "operationId":  "GetSensorInstallersEntities",
        "path":  "/sensors/entities/installers/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Download",
                         "command":  "Get-FalconInstaller -Id"
                     }
    },
    {
        "collection":  "sensors",
        "operationId":  "GetSensorInstallersCCIDByQuery",
        "path":  "/sensors/queries/installers/ccid/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Download",
                         "command":  "Get-FalconCcid"
                     }
    },
    {
        "collection":  "sensors",
        "operationId":  "GetSensorInstallersByQuery",
        "path":  "/sensors/queries/installers/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Sensor-Download",
                         "command":  "Get-FalconInstaller"
                     }
    },
    {
        "collection":  "settings",
        "operationId":  "GetCSPMPolicy",
        "path":  "/settings/entities/policy-details/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonPolicy -Id"
                     }
    },
    {
        "collection":  "settings",
        "operationId":  "GetCSPMPolicySettings",
        "path":  "/settings/entities/policy/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonPolicy"
                     }
    },
    {
        "collection":  "settings",
        "operationId":  "UpdateCSPMPolicySettings",
        "path":  "/settings/entities/policy/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Edit-FalconHorizonPolicy -Severity -Enabled -Id"
                     }
    },
    {
        "collection":  "settings",
        "operationId":  "GetCSPMScanSchedule",
        "path":  "/settings/scan-schedule/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Get-FalconHorizonSchedule"
                     }
    },
    {
        "collection":  "settings",
        "operationId":  "UpdateCSPMScanSchedule",
        "path":  "/settings/scan-schedule/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Horizon",
                         "command":  "Edit-FalconHorizonSchedule -ScanSchedule -CloudPlatform"
                     }
    },
    {
        "collection":  "spotlight",
        "operationId":  "combinedQueryEvaluationLogic",
        "path":  "/spotlight/combined/evaluation-logic/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Spotlight",
                         "command":  "Get-FalconVulnerabilityLogic -Filter -Detailed"
                     }
    },
    {
        "collection":  "spotlight",
        "operationId":  "combinedQueryVulnerabilities",
        "path":  "/spotlight/combined/vulnerabilities/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Spotlight",
                         "command":  "Get-FalconVulnerability -Filter -Detailed"
                     }
    },
    {
        "collection":  "spotlight",
        "operationId":  "getEvaluationLogic",
        "path":  "/spotlight/entities/evaluation-logic/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Spotlight",
                         "command":  "Get-FalconVulnerabilityLogic -Id"
                     }
    },
    {
        "collection":  "spotlight",
        "operationId":  "getRemediationsV2",
        "path":  "/spotlight/entities/remediations/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Spotlight",
                         "command":  "Get-FalconRemediation -Id"
                     }
    },
    {
        "collection":  "spotlight",
        "operationId":  "getVulnerabilities",
        "path":  "/spotlight/entities/vulnerabilities/v2",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Spotlight",
                         "command":  "Get-FalconVulnerability -Id"
                     }
    },
    {
        "collection":  "spotlight",
        "operationId":  "queryEvaluationLogic",
        "path":  "/spotlight/queries/evaluation-logic/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Spotlight",
                         "command":  "Get-FalconVulnerabilityLogic -Filter"
                     }
    },
    {
        "collection":  "spotlight",
        "operationId":  "queryVulnerabilities",
        "path":  "/spotlight/queries/vulnerabilities/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Spotlight",
                         "command":  "Get-FalconVulnerability -Filter"
                     }
    },
    {
        "collection":  "user-roles",
        "operationId":  "GetRoles",
        "path":  "/user-roles/entities/user-roles/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Get-FalconRole -Id"
                     }
    },
    {
        "collection":  "user-roles",
        "operationId":  "GrantUserRoleIds",
        "path":  "/user-roles/entities/user-roles/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Add-FalconRole -UserId -Id"
                     }
    },
    {
        "collection":  "user-roles",
        "operationId":  "RevokeUserRoleIds",
        "path":  "/user-roles/entities/user-roles/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Remove-FalconRole -UserId -Id"
                     }
    },
    {
        "collection":  "user-roles",
        "operationId":  "GetAvailableRoleIds",
        "path":  "/user-roles/queries/user-role-ids-by-cid/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Get-FalconRole"
                     }
    },
    {
        "collection":  "user-roles",
        "operationId":  "GetUserRoleIds",
        "path":  "/user-roles/queries/user-role-ids-by-user-uuid/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Get-FalconRole -UserId"
                     }
    },
    {
        "collection":  "users",
        "operationId":  "RetrieveUser",
        "path":  "/users/entities/users/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Get-FalconUser -Id"
                     }
    },
    {
        "collection":  "users",
        "operationId":  "CreateUser",
        "path":  "/users/entities/users/v1",
        "method":  "post",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "New-FalconUser -Username"
                     }
    },
    {
        "collection":  "users",
        "operationId":  "DeleteUser",
        "path":  "/users/entities/users/v1",
        "method":  "delete",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Remove-FalconUser -Id"
                     }
    },
    {
        "collection":  "users",
        "operationId":  "UpdateUser",
        "path":  "/users/entities/users/v1",
        "method":  "patch",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Edit-FalconUser -Id"
                     }
    },
    {
        "collection":  "users",
        "operationId":  "RetrieveEmailsByCID",
        "path":  "/users/queries/emails-by-cid/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  null,
                         "command":  null
                     }
    },
    {
        "collection":  "users",
        "operationId":  "RetrieveUserUUIDsByCID",
        "path":  "/users/queries/user-uuids-by-cid/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Get-FalconUser"
                     }
    },
    {
        "collection":  "users",
        "operationId":  "RetrieveUserUUID",
        "path":  "/users/queries/user-uuids-by-email/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Users-and-Roles",
                         "command":  "Get-FalconUser -Username"
                     }
    },
    {
        "collection":  "zero-trust-assessment",
        "operationId":  "getAssessmentV1",
        "path":  "/zero-trust-assessment/entities/assessments/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Zero-Trust-Assessment",
                         "command":  "Get-FalconZta -Id"
                     }
    },
    {
        "collection":  "zero-trust-assessment",
        "operationId":  "getComplianceV1",
        "path":  "/zero-trust-assessment/entities/audit/v1",
        "method":  "get",
        "psfalcon":  {
                         "link":  "https://github.com/crowdstrike/psfalcon/wiki/Zero-Trust-Assessment",
                         "command":  "Get-FalconZta"
                     }
    }
]