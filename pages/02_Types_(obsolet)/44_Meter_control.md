:::sidecode
## Example of meter control

```json
{
	"@label": "Temperature",
	"min": 0,
	"max": 30,
	"units": "Degress"
}
```
:::

## Meter control
`application/x.meta.control.number.meter+json`

Control which describes current measured value and target value.

Inherits from `application/x.meta.control.number+json` control.

Should be displayed as gauge or range.

| Property name | Type   | Description           | Required |
| ------------- | ------ | --------------------- | -------- |
| units         | string | Units                 | No |

**Model properties**
| Property name | Type   | Description            |
| ------------- | ------ | ---------------------- |
| value         | number | Current set value      |
| state         | number | Current measured value |