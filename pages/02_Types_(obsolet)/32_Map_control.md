:::sidecode
## Example of map control

```json
{
	"@label": "Tags",
	"layout": "./tag.meta",
	"key": "label",
	"minItems": 1,
	"maxItems": 10
}
```
:::

## Map control
`application/x.meta.control.map+json`

Same as `list` control but represents object with keys (map).

This control requires `layout` to be defined. Child layout model will be added to list as object.

Value of this control is `object`.

Should be displayed with `+` and `-` buttons.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| layout 		| uri     | URI of property list. Must be compatible with mime type: `application/json+meta.properties` | Yes |
| key 	        | string  | Which property should be used as map key. | Yes |
| minItems      | integer | Minimum number of items that must be present in list - defaults to `0` | No |
| maxItems      | integer | Maximum number of items that can be present in list. | No |

:::clear :::