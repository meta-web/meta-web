:::sidecode
## Example

```json
{
	"@doctype": "meta/resource",
	"$c": {
		"@type": "meta/data",
		"uri": "./42.json"
	},
	"label: "{{$c.first_name}} {{$c.last_name}}",
	"properties": [
		{
			"@type": "meta/properties/text",
			"label": "First name",
			"required": true,
			"model": "$c.first_name"
		}
	]
}
```
:::

## Resource properties

Resource properties describes object and are specified as **`properties`** property of document.

See [Properties](../properties/) page for specification of object property types.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| properties | Array of Object | Yes | No | Properties definition |