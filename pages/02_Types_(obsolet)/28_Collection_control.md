:::sidecode
## Example of collection control

```json
{
	"@label": "Categories",
	"collection": "./categories.meta",
	"key": "id",
	"maxItems": 3
}
```
:::

## Collection control
`application/x.meta.control.collection+json`

Same as optons control but items are fetched from MetaWeb collection.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| collection 	| uri     | URI of collection from which options will be fetched. Must be compatible with mime type: `application/x.meta.collection+json` | Yes |
| key           | string  | Property of record model which will be used as option value | Yes |
| minItems      | integer | Minimum number of selected items. Defaults to `0`.  | No |
| maxItems      | integer | Maximum number of selected items. Defaults to `1`. If set to `-1` then infinite count of selected items is allowed. | No |
| @style        | string  | Defines how to display control - one of (dropdown / list / grid). Defaults to 'dropdown'. | No |