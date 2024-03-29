# ConvertTo-FalconFirewallRule
## SYNOPSIS
Convert firewall rules to be compatible with Falcon Firewall Management
## DESCRIPTION
Ensures that an object (either from the pipeline, or via CSV import) has the required properties to be accepted
as a valid Falcon Firewall Management rule.

Rules that contain both IPv4 and IPv6 addresses will generate errors, along with any rules that are missing the
required properties defined by the 'Map' parameter.

Converted rules used with 'New-FalconFirewallGroup' to create groups containing newly converted rules.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Map|Hashtable|A hashtable containing the following keys with the corresponding CSV column or rule property as the value<BR><BR>Required: action, description, direction, enabled, local_address, local_port, name, remote_address, remote_port<BR>Optional: image_name, network_location, service_name||||||
|Path|String|Path to a CSV file containing rules to convert||||||
|Object|Object|An existing rule object to convert||||X||
## SYNTAX
```powershell
ConvertTo-FalconFirewallRule [-Map] <Hashtable> [-Path] <String> [<CommonParameters>]
```
```powershell
ConvertTo-FalconFirewallRule [-Map] <Hashtable> -Object <Object> [<CommonParameters>]
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
