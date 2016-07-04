:::sidecode
## Example

```json
{
	"@doctype": "meta/resource",
	"$c": {
		"@type": "meta/data",
		"uri": "./42.json"
	},
	"label: "{{$c.first_name}} {{$c.last_name}}",
    "aliases": [ "Customer" ],
    "icon": "/assets/customer.svg",
    "schema": "entity.person.customer",
    "readonly": "$c.editable",
    "parent": "../index.meta",
    "previous": "./41.meta",
    "next": "./43.meta",
    "sitemap": "/sitemap.meta",
    "manifest": "/manifest.meta",
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
			"uri": "./42.json",
			"model": "$c",
			"label": "Update",
			"icon": "/assets/save.svg",
			"schema": "@update"
		},
		{
			"method": "navigate",
			"uri": "../related",
			"model": {
				"customer": "$c.id"
			},
			"label": "Related entires",
			"icon": "/assets/link.svg",
			"schema": "@related"
		}
	]
}
```
:::

## Resource actions

Every resource can specify actions which can be invoked on that resource and are specified as **`actions`** property of document.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| actions | Array of Object | No | No | Actions definition |

### Action definition

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| method | String | Yes | No | HTTP method + specials |
| uri | String / URI | Yes | Yes | URI which will be called when action will be invoked |
| model | String | Object | No | No | Model property which will be submitted to target URI. Entire document model will be used by default. When defined as object then each key will represent data property name and value must reference to document model. |
| label | String | Yes | Yes | Label of action |
| aliases | Array of String | No | Yes | Alternative action labels |
| icon | String / URI | No | No | URI to resource icon, all image formats are supported but SVG is recommended |
| schema | String | No | No | MetaWEB schema identifier from [Schema vocabulary](../schema-vocabulary/) |
| context | String | No | No | Where to display action, one of `main`, `options`. |
| style | String | No | No | How to display action result, one of `default`, `dialog`. |

::: info
To submit no data specify `model` as empty object, eg.: `{}`.
:::

::: warning
Except `navigate` method all actions should be processed without redirecting client to target URI.
:::

### Supported methods

| Method | Data format | Description |
| ------ | ----------- | ----------- |
| GET | Query string | Makes GET HTTP request and submits data as query string |
| POST | JSON body | Makes POST HTTP request and submits data as JSON encoded body |
| PUT | JSON body | Makes PUT HTTP request and submits data as JSON encoded body |
| DELETE | JSON body | Makes DELETE HTTP request and submits data as JSON encoded body |
| navigate | Query string | Redirects client to target URI with data encoded as query string |

::: warning
**Response**  
Response should be compatible with [Response type](../api/#10_Action_response). Otherwise response content should be displayed as text.
:::