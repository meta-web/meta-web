:::sidecode
## Example of property definition

```json
{
	"@doctype": "meta/resource",
	"$customer": {
		"@type": "meta/data",
		"uri": "./customer.json"
	},
	"$isNew": {
		"@type": "meta/javascript",
		"args": [ "$customer" ],
		"value": "return ($customer.active > $now ? true : false);"
	},
	"$now": {
		"@type": "meta/javascript",
		"args": [],
		"uri": "./now.js"
	},
	"$value": {
		"@type": "meta/data",
		"value": 123
	}
}
```
:::

## Data binding

Resource type describes object behaviour but data are seperated into another layer and are binded as specified.

When resource is loaded then data model is created.

Data binding is based on definition of model properties.

Each **model property** is defined as **document property** of object type which is prefixed with **`$`** dollar sign.

Model property can be one of following:

- Datasource
- JavaScript function (with limited scope)
- Inline defined value

Datasource and JavaScript propreties can be external and referenced by URI.

### Model definition

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- | 
| @type | String | Yes | No | Type of model property, one of: `meta/data`, [`meta/datasource`](../api/#02_Collection_datasource), `meta/javascript` |
| uri | String / URI | Yes if external | No | URI of model resource |
| value | JSON any | Yes if not external | No | Model property value |
| args | Array of String | Yes if JavaScript type | No | Model properties as input arguments |

::: warning
When both `uri` and `value` is specified then `value` is used. You should never specify both properties together.
:::

### JavaScript functions

- JavaScript code is loaded as anonymous function body
- Function return value is binded as model property
- Function can accept another model properties as input arguments
- Function output cannot be also it's input (eg. recursive functions are not allowed)
- When any of input model properties has changed then function is re-run and it's output is re-binded
- Functions has no access to standard DOM or browser objects, just vanilla JS