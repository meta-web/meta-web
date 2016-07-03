:::sidecode
## Example of collection file

```json
{
	"label": "User profiles",
	"icon": "./users.svg",
	"style": "list",
	"model": "./users.json",
	"layout": "./userRecord.meta",
	"multiselect": true,
	"@embed": {
		"./userRecord.meta": {
			"@mimeType": "application/x.meta.layout+json",
			"controls": [
				{
					"uri": "#first_name",
					"model": "model:$first_name"
				},
				{
					"uri": "#last_name",
					"model": "model:$last_name"
				},
				{
					"uri": "#is_vip",
					"model": "model:$is_vip"
				}
			]
		},
		"./userRecord.meta#first_name": {
			"@mimeType": "application/x.meta.control.text+json",
			"label": "First name"
		},
		"./userRecord.meta#last_name": {
			"@mimeType": "application/x.meta.control.text+json",
			"label": "Last name"
		},
		"./userRecord.meta#is_vip": {
			"@mimeType": "application/x.meta.control.boolean+json",
			"label": "Is VIP",
			"style": "switch"
		}
	}
}
```
:::

## Collection {.tag .get}

Collection defines list of records and should provide pagination and filtering.

| Feature | Value |
| ------- | ----- |
| Mime-type | `application/x.meta.collection+json` |
| Cachable | Yes |

### Collection properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| label         | string | Title of current resource - should be displayed in user interface | No |
| icon          | string | Icon (for user interface) - should be URI to SVG file | No |
| style         | string | Type of UI display type, one of (list / grid) | No |
| model         | uri    | URI where to fetch collection records - response must be compatible with mime type: `application/x.meta.collection.records+json` | Yes |
| layout        | uri    | URI of resource which defines record layout with mime type `application/x.meta.layout+json`. Record model is passed to layout. | Yes |
| multiselect   | boolean | If records can be selected for bulk actions | No |

::: info
**Filters and sorting** {.title}

Should be specified.
:::

:::clear :::