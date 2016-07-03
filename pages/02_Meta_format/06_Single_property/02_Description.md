:::sidecode
## Example of collection type as stand-alone resource

```json
{
	"@doctype": "meta/property",
	"@type": "meta/properties/collection",
	"label": "Customers",
	"alises": [ "Customer", "collection" ],
	"icon": "/assets/customer.svg",
	"$datasource": {
		"@type": "meta/datasource",
		"uri": "customers.php"
	},			
	"datasource": "$$datasource",
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
	},
	"minItems": 0,
	"maxItems": -1,
	"style": "list",
	"filters": [
		{
			"@type": "meta/properties/text",
			"label": "Name",
			"model": "$name"
		}
	],
	"actions": [
		{
            "method": "NAVIGATE",
            "uri": "./add.meta",
            "label": "Add customer",
            "icon": "/assets/add.svg",
            "schema": "@create",
            "style": "dialog"
		},
		{
            "method": "DELETE",
            "uri": "./customers.php",
            "model": "$selection",
            "label": "Trash",
            "icon": "/assets/trash.svg",
            "schema": "@delete"
		}
	]
}
```
:::

## Description
**`@doctype: meta/property`**

Property document type derives from [`meta/resource`](../resource/) type and any of [`meta/properties`](../properties/) type.

All `meta/resource` properties are supported except `properties` property.

All `meta/properties/*` properties are supported except descriptive properties.