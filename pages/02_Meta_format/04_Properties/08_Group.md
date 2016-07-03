:::sidecode
## Example of Group property

```json
{
	"@type": "meta/properties/group",
	"label": "Personal information",
	"properties": [
		{
			"@type": "meta/properties/text",
			"label": "First name",
			"model": "$first_name",
			"required": true
		},
		{
			"@type": "meta/properties/text",
			"label": "Last name",
			"model": "$last_name",
			"required": true
		}
	]
}
```
:::

## Group property

**`@type: meta/properties/group`**

Group of another properties.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| properties | Array of Object | Yes | No | Child properties array |