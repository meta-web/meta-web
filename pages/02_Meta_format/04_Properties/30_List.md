:::sidecode
## Example of list property

```json
{
	"@type": "meta/properties/list",
	"label": "Attachments",
	"template": {
		"@doctype": "meta/resource",
		"label": "Attachment",
		"properties": [
			{
				"@type": "meta/properties/text",
				"label": "Name",
				"model": "$name",
				"required": true
			},
			{
				"@type": "meta/properties/file",
				"label": "File",
				"model": "$file",
				"required": true
			}
		]
	},
	"maxItems": 10
}
```

## Example of list property as map

```json
{
	"@type": "meta/properties/map",
	"label": "Attributes",
	"key": "$name",
	"template": {
		"@doctype": "meta/resource",
		"label": "Attribute",
		"properties": [
			{
				"@type": "meta/properties/text",
				"label": "Name",
				"model": "$name",
				"required": true
			},
			{
				"@type": "meta/properties/text",
				"label": "Value",
				"model": "$value",
				"required": true
			}
		]
	}
}
```
:::

## List property

**`@type: meta/properties/list`**

Property which represents dynamic list of items.

When `key` is specified then list works as `map`, eg. key-value.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| template | String / URI, Object | Yes | No | URI to template document or document template embedded as object. Template model is used as item object |
| key | String | No | No | Item model property which is used as map key for item |
| minItems | Integer | No | No | Minimum number of items to be valid. Defaults to `0` |
| maxItems | Integer | No | No | Maximum number of items. Defaults to `-1`. If set to `-1` then infinite count of selected items is allowed |

::: warning
**Model**  
Initial model must be an array of objects or object of objects (map) which are passed to template as root model.
:::