:::sidecode
## Example of number property

```json
{
	"@type": "meta/properties/number",
	"label": "Age",
	"min": 1,
	"max": 128,
	"decimal": 0,
	"style": "range"
}
```
:::

## Number property

**`@type: meta/properties/number`**

Basic numeric property

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| min      | Float   | No | No | Minimum input value |
| max 	   | Float   | No | No | Maximum input value |
| decimal  | Integer | No | No | Count of allowed decimal places |
| style    | String  | No | No | Defines how to display control - one of (input / range / gauge) |