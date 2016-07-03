:::sidecode
## Example of collection property

```json
{
	"@doctype": "meta/resource",
	"label: "Customers",
	"$datasource": {
		"@type": "meta/datasource",
		"uri": "customers.php"
	},
	"properties": [
		{
			"@type": "meta/properties/collection",
			"label": "Customer list",
			"datasource": "$$datasource",
			"template": "./record.meta",
			"model": "$list",
			"minItems": 0,
			"maxItems": -1,
			"style": "list",
			"filters": [
				{
					"@type": "meta/properties/text",
					"label": "Name",
					"model": "$name"
				}
			]
		}
	],
	"actions": [
		{
            "method": "DELETE",
            "uri": "./customers.php",
            "model": "$list.selection",
            "label": "Trash",
            "icon": "/assets/trash.svg",
            "schema": "@delete"
		}
	]
}
```

## Example of embedded template

```json
{
	"@doctype": "meta/resource",
	"label: "Customers",
	"properties": [
		{
			"@type": "meta/properties/collection",
			"label": "Customer list",
			"style": "grid",
			"$datasource": {
				"@type": "meta/datasource",
				"uri": "customers.php"
			},
			"datasource": "$datasource",
			"template": {
				"@doctype": "meta/resource",
				"label": "{{$first_name}} {{$last_name}}",
				"image": "./image.php?id={{$id}}",
				"properties": [
					{
						"@type": "meta/properties/text",
						"label": "First name",
						"model": "$first_name",
						"readonly": true
					},
					{
						"@type": "meta/properties/text",
						"label": "Last name",
						"model": "$last_name",
						"readonly": true
					}
				],
				"action": [
					{
						"method": "navigate",
						"label": "Detail",
						"uri": "./{{$id}}.meta"
					}
				]
			}
		}
	]
}
```
:::

## Collection property

**`@type: meta/properties/collection`**

Advanced property which represents collection of records a displays them as complex objects.

**Collection should support:**

- Pagination*
- Filtering*
- Selection of records

* Depends on datasource

### Configuration properties

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| datasource | String | Yes | No | Model property to collection records |
| template | String / URI, Object | Yes | No | URI to template document or document template embedded as object. Record object is passed to template as root model |
| filters | Array of Object | No | No | [Document properties](../properties/) displayed as filters. Filter properties has it's own independent model |
| key | String | No | No | Export specified record's key to selection model instead of entire object |
| minItems | Integer | No | No | Minimum number of selected items. Defaults to `0` |
| maxItems | Integer | No | No | Maximum number of selected items. Defaults to `1`. If set to `-1` then infinite count of selected items is allowed |
| style    | String  | No | No | Defines how to display control - one of `list`, `grid`. Defaults to `list`

::: warning
**Datasource**  
Datasource must be an object or an array.

If datasource is array then collection should implement filtering and ordering internaly on client side.

If datasource is of type `meta/datasource` then pagination, filtering and ordering must be provided on server side as specified in `meta/datasource` documentation.
:::

### Model

Collection exports following properties to it's model:

| Property | Type | Description |
| -------- | ---- | ----------- |
| selection | Array of Object | Selected record objects |
| filters | Object | Model of filter properties |