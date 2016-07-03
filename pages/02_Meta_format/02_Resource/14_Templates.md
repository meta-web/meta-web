:::sidecode
## `customers/template.meta`

```json
{
	"@doctype": "meta/resource",
	"label: "{{$c.first_name}} {{$c.last_name}}",
    "readonly": "$c.editable",
    "previous": "../{{$c.prev_id}}.json",
    "next": "../{{$c.next_id}}.json",
	"properties": [
		{
			"@type": "meta/properties/text",
			"label": "First name",
			"required": true,
			"model": "$c.first_name"
		},
		{
			"@type": "meta/properties/text",
			"label": "last name",
			"required": true,
			"model": "$c.last_name"
		}
	],
	"actions": [
		{
			"method": "PUT",
			"uri": "./{{$c.id}}.json",
			"model": "$c",
			"label": "Update",
			"icon": "/assets/save.svg",
			"schema": "@update"
		}
	]
}
```

## `customers/42.meta`

```json
{
	"@doctype": "meta/resource",
	"template": "./template.meta",
	"$c": {
		"@type": "meta/data",
		"uri": "./42.json"
	}
}
```

## Final document

```json
{
	"@doctype": "meta/resource",
	"label: "{{$c.first_name}} {{$c.last_name}}",
    "readonly": "$c.editable",
    "previous": "../{{$c.prev_id}}.json",
    "next": "../{{$c.next_id}}.json",
	"properties": [
		{
			"@type": "meta/properties/text",
			"label": "First name",
			"required": true,
			"model": "$c.first_name"
		},
		{
			"@type": "meta/properties/text",
			"label": "last name",
			"required": true,
			"model": "$c.last_name"
		}
	],
	"actions": [
		{
			"method": "PUT",
			"uri": "./{{$c.id}}.json",
			"model": "$c",
			"label": "Update",
			"icon": "/assets/save.svg",
			"schema": "@update"
		}
	],
	"$c": {
		"@type": "meta/data",
		"uri": "./42.json"
	}
}
```
:::

## Templates

Returning full MetaWEB file for every record in collection is wasting of bandwith and resources.

MetaWEB resource type provides possibility to define **template file** which can be loaded once, cached and reused in another simplified MetaWEB files.

Template can be specified as URI to another MetaWEB file of same type. When specified client must load template document at first and then override properties specified in current document.

See example for better understanding.