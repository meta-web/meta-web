:::sidecode
## Example of number control

```json
{
	"@label": "Price",
	"style": "range",
	"min": 5,
	"max": 32,
	"decimal": 2
}
```
:::

## Number control
`application/x.meta.control.number+json`

Basic number input control

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| min           | float   | Minimum input value   | No |
| max 	        | float   | Maximum input value   | No |
| decimal  		| integer | Count of allowed decimal places | No |
| style         | string  | Defines how to display control - one of (input / range / gauge) | No |