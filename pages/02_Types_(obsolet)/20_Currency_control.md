:::sidecode
## Example of currency control

```json
{
	"@label": "Price",
	"min": 0,
	"max": 1000,
	"decimal": 2,
	"currency": "CZK"
}
```
:::

## Currency control
`application/x.meta.control.number.currency+json`

Currency input control. Inherits from `application/x.meta.control.number+json` control.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| currency      | string  | Currency label        | No |