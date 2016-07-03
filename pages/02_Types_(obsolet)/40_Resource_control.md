:::sidecode
## Example of Resource control

```json
{
	"@label": "Profile",
	"select": "http://www.identity.meta/profiles/index.meta",
	"pattern": "^http:\/\/www.identity.meta\/profiles\/*$",
	"multiple": true,
	"minItems": 1,
	"maxItems": 5
}
```
:::

## Resource control

`application/x.meta.control.resource+json`  

Control which represents MetaWEB resource. Can be displayed as text input or as selector of available resources.

| Property name | Type   | Description           | Required |
| ------------- | ------ | --------------------- | -------- |
| select        | uri    | URI to `application/x.meta.layout+json` or `application/x.meta.sitemap+json` resources which can be loaded and displayed as menu. | No |
| pattern  		| string | Validation RegExp     | No |
| multiple      | boolean | If multiple selection is allowed. If `true` then model value will be an array. | No |
| minItems      | integer | Minimume number of selected items. Defaults to `0`. | No |
| maxItems      | integer | Maximum number of selected items. Defaults to `1`. If set to `-1` then infinite count of selected items is allowed. | No |