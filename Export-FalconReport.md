# Export-FalconReport
## SYNOPSIS
Format a response object and output to console or CSV
## DESCRIPTION
Each property within a response object is 'flattened' to a single field containing a CSV-compatible value--with
each column having an appended 'prefix'--and then exported to the console or designated file path.

For instance, if the object contains a property called 'device_policies', and that contains other objects called
'prevention' and 'sensor_update', the result will contain properties labelled 'device_policies.prevention' and
'device_policies.sensor_update' with additional '.<field_name>' values for any sub-properties of those objects.

When the result contains an array with similarly named properties, it will attempt to add each sub-property with
an additional 'id' prefix based on the value of an existing 'id' or 'policy_id' property. For example,
@{ hosts = @( @{ device_id = 123; hostname = 'abc' }, @{ device_id = 456; hostname = 'def' })} will be displayed
under the columns 'hosts.123.hostname' and 'hosts.456.hostname'. The 'device_id' property is excluded as it
becomes a column.

There is potential for data loss due to object manipulation. Use 'ConvertTo-Json' to ensure all object properties
are retained when integrity is a concern.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Destination path||||||
|Object|Object[]|Response object to format||||X||
## SYNTAX
```powershell
Export-FalconReport [[-Path] <String>] [-Object] <Object[]> [<CommonParameters>]
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
