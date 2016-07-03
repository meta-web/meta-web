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
	"aliases": [ "Customer", "{{$c.address}}" ],
	"icon": "/assets/customer.svg",
	"schema": "entity.person.customer",
	"readonly": "$c.locked"
}
```
:::

## Descriptive properties

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| label | String | Yes | Yes | Label of resource |
| alises | Array of String | No | Yes | Alternative resource labels, eg. different forms of words - helpful for voice control |
| icon | String / URI | No | No | URI to resource icon, all image formats are supported but SVG is recommended |
| image | String / URI | No | No | URI to resource header image, all image formats are supported. Bitmap formats recommended. |
| schema | String | No | No | MetaWEB schema identifier from [Schema vocabulary](../schema-vocabulary/) |
| readonly | Boolean / Model prop. as String | No | No | If resource is read-only and thus all controls must be disabled. |