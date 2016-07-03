:::sidecode
## Example of options property

```json
{
	"@type": "meta/properties/options",
	"label": "Role",
	"style": "switch",
	"options": [
		{
			"value": "1",
			"label": "Visitor",
			"alises": [ "Guest" ],
			"icon": "/assets/visitor.svg"
		},
		{
			"value": "2",
			"label": "Moderator",
			"icon": "/assets/moderator.svg"
		},
		{
			"value": "3",
			"label": "Administrator",
			"aliases": [ "Admin" ],
			"icon": "/assets/admin.svg"
		}
	],
	"maxItems": 3
}
```
:::

## Options property

**`@type: meta/properties/options`**

Property which selects from predefined values.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| options | Array of Object | No | No | Array of available options |
| optionsUri | String / URI | No | Yes | Alternatively options can be specified as URI. Referenced resource must be JSON in `options` config format |
| minItems | Integer | No | No | Minimum number of selected items. Defaults to `0` |
| maxItems | Integer | No | No | Maximum number of selected items. Defaults to `1`. If set to `-1` then infinite count of selected items is allowed |
| style    | String  | No | No | Defines how to display control - one of (dropdown / inline / switch). Defaults to `dropdown`

### Option item properties

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| value | Any | Yes | No | Item value |
| label | String | Yes if not separator | Yes | Item label |
| aliases | Array of String | No | Yes | Alternative property labels, eg. different forms of words - helpful for voice control |
| icon | String / URI | No | No | URI to item icon, all image formats are supported but SVG is recommended |
| separator | Boolean | No | No | Display item as separator. Value is then ignored and if label is set then separator shoud by displayed as group title |