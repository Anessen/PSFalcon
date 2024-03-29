# Edit-FalconDeviceControlPolicy
## SYNOPSIS
Modify Falcon Device Control policies
## DESCRIPTION
Requires 'Device control policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to modify in a single request||||X||
|Id|String|Policy identifier||||||
|Name|String|Policy name||||||
|Description|String|Policy description||||||
|Setting|Object|Policy settings||||||
|Default|Switch|Modify the default Windows Device Control policy||||||
|Blocked|String|Custom notification for blocked events||||||
|UseBlocked|Boolean|Enable custom notification for blocked events||||||
|Restricted|String|Custom notification for restricted events||||||
|UseRestricted|Boolean|Enable custom notification for restricted events||||||
## SYNTAX
```powershell
Edit-FalconDeviceControlPolicy [-Id] <String> [[-Name] <String>] [[-Description] <String>] [[-Setting] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconDeviceControlPolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconDeviceControlPolicy -Default [[-Blocked] <String>] [[-UseBlocked] <Boolean>] [[-Restricted] <String>] [[-UseRestricted] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /policy/entities/default-device-control/v1
PATCH /policy/entities/device-control/v1
```
### falconpy
[updateDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#updateDeviceControlPolicies)<BR>[updateDefaultDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#updateDefaultDeviceControlPolicies)
## USAGE
### Enable policy settings
```powershell
$Setting = @{
    enforcement_mode = 'MONITOR_ENFORCE'
    end_user_notifications = 'NOTIFY_USER'
    classes = @(
        @{
            id = 'AUDIO_VIDEO'
            action = 'BLOCK_ALL'
            exceptions = @(
                @{
                    combined_id = '1133_2092_7A4F8BD0'
                    action = 'FULL_ACCESS'
                    expiration_time = '2023-01-01T00:00:00Z'
                }
            )
        },
        @{
            id = 'MASS_STORAGE'
            action = 'BLOCK_ALL'
            exceptions = @(
                @{
                    vendor_id = '59f'
                    vendor_name = 'LaCie'
                    product_id = '10c4'
                    product_name = 'HDD'
                    action = 'BLOCK_EXECUTE'
                },
                @{
                    vendor_id_decimal = '3010'
                    vendor_name = 'Seagate'
                    action = 'FULL_ACCESS'
                }
            )
        }
    )
}
Edit-FalconDeviceControlPolicy -Id <id> -Setting $Setting
```
### Create or add exceptions
```powershell
$Setting = @{
    classes = @(
        @{
            id = 'ANY'
            exceptions = @(
                @{
                    action = 'BLOCK_ALL'
                    combined_id = '1_2_345'
                },
                @{
                    action = 'BLOCK_ALL'
                    vendor_id_decimal = '6'
                    vendor_name = 'Example Vendor'
                    product_id_decimal = '7'
                    product_name = 'Example Product'
                    serial_number = '891'
                }
            )
        },
        @{
            id = 'IMAGING'
            action = 'BLOCK_ALL'
            exceptions = @(
                @{
                    action = 'FULL_ACCESS'
                    combined_id = '5_4_321'
                },
                @{
                    action = 'FULL_ACCESS'
                    vendor_id_decimal = '20'
                    vendor_name = 'Example Vendor 2'
                    product_id_decimal = '30'
                    product_name = 'Example Product 2'
                },
            )
        },
        @{
            id = 'MASS_STORAGE'
            action = 'BLOCK_ALL'
            exceptions = @(
                @{
                    action = 'FULL_ACCESS'
                    combined_id = '5_4_321'
                },
                @{
                    action = 'FULL_ACCESS'
                    vendor_id_decimal = '30'
                    vendor_name = 'Example Vendor 3'
                },
            )
        }
    )
}
Edit-FalconDeviceControlPolicy -Id <id> -Setting $Setting
```
_See [Add a list of combined_id exceptions to a Device Control policy](https://github.com/CrowdStrike/psfalcon/blob/master/samples/policies/add-a-list-of-combined_id-exceptions-to-a-device-control-policy.ps1)._
### Remove exceptions from a policy
```powershell
$Setting = @{ delete_exceptions = @('id', 'id') }
Edit-FalconDeviceControlPolicy -Id <id> -Setting $Setting
```
**NOTE**: The required `id` values can be found under the `settings.classes.exceptions` sub-object. Classes can be filtered by their relevant `id` values to find the specific exceptions for that class type.
```powershell
$Policy = Get-FalconDeviceControlPolicy -Id <id>
$Policy.settings.classes.Where({ $_.id -eq 'MASS_STORAGE' }).exceptions
```
_See [Create CSVs containing Device Control policy details and exceptions](https://github.com/CrowdStrike/psfalcon/blob/master/samples/policies/create-csvs-containing-device-control-policy-details-and-exceptions.ps1)._

_2023-04-25: PSFalcon v2.2.5_
