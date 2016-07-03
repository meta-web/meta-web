:::sidecode
## Example of Meter property

```json
{
	"@type": "meta/properties/number/meter",
	"label": "Temperature",
	"min": 0,
	"max": 30,
	"units": "°C"
}
```
:::

## Meter property

**`@type: meta/properties/number/meter`** extends **`meta/properties/number`**

Meter property represents measured and target value.

Usable for temperature, pressure, speed or other controls.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| units    | String | Yes | Yes | Units |

::: info
**UI**  
Client can display this property as gauge.
:::

### Model properties
| Property name | Type   | Description            |
| ------------- | ------ | ---------------------- |
| value         | Number | Current set value      |
| state         | Number | Current measured value |