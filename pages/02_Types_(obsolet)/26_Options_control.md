:::sidecode
## Example of options control

```json
{
	"@label": "Categories",
	"@style": "inline",
	"options": {
		"dogs": "Dogs",
		"cats": "Cats"
	},
	"optionsModel": "./categories.json",
	"maxItems": 3
}
```
:::

## Options control
`application/x.meta.control.options+json`

Control which provides selection of specified options.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| options       | object  | List of available options as object in format `"key": "value"`. | Yes |
| optionsUri 	| uri     | Options can be also specified as model URI. Data must be compatible with `options` property format. | No |
| minItems      | integer | Minimum number of selected items. Defaults to `0`.  | No |
| maxItems      | integer | Maximum number of selected items. Defaults to `1`. If set to `-1` then infinite count of selected items is allowed. | No |
| style        | string  | Defines how to display control - one of (dropdown / inline / switch). Defaults to `dropdown` | No |