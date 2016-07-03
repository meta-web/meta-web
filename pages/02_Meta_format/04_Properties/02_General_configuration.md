:::sidecode
## Example of property definition

```json
{
	"@type": "meta/property/text",
	"@context": "main",
	"id": "first_name",
	"label": "First name",
	"aliases": [ "{{$value}}" ],
	"icon": "/assets/prop.svg",
	"schema": "entity.person.name.first",
	"model": "$c.first_name",
	"required": true,
	"readonly": "$$c.editable",
	"hidden": "$isHidden",
	"$isHidden": {
		"@type": "meta/javascript",
		"value": "return (Math.random() > 0.5 ? true : false)"
	}
}
```
:::

## General configuration

Each property is defined by common configuration properties which are same for all types.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| @type | String | Yes | No | Control type ID |
| @context | String | No | No | Where to display control, one of `main`, `header`, `footer`, `aside`. Defaults to `main` |
| id | String | No | No | Property ID - usable for parsing |
| label | String | Yes | Yes | Label of property |
| alises | Array of String | No | Yes | Alternative property labels, eg. different forms of words - helpful for voice control |
| icon | String / URI | No | No | URI to property icon, all image formats are supported but SVG is recommended |
| schema | String | No | No | MetaWEB schema identifier from [Schema vocabulary](../schema-vocabulary/) |
| model | String | No | No | Specifies model scope passed to property control. Document model is default. |
| required | Boolean / Model prop. as String | No | No | If property is required |
| readonly | Boolean / Model prop. as String | No | No | If property is read-only and thus control and it's children must be disabled. |
| hidden | Boolean / Model prop. as String | No | No | If property must be hidden |
| $* | Object | No | No | Model property |

::: info
**Model scope**  
When model scope is defined then top document model is always accessible via **`$$`** property.
:::