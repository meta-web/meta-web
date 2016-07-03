## Date and time controls

Values must be ISO-8601 compatible or expression.

::: info
**Expression**

Expression is used with `$now` variable and can specify past or future date or time (depends on control type).

`$now-0000-01-00`
`$now+0000-01-00`
`$now`
:::

:::sidecode
## Example of date control

```json
{
	"@label": "Date",
	"min": "$now",
	"max": "2016-12-01"
}
```
:::

### Date control
`application/x.meta.control.date+json`

Date input control.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| min           | string  | Minimum input value   | No |
| max 	        | string  | Maximum input value   | No |

:::clear :::

:::sidecode
## Example of time control

```json
{
	"@label": "Start",
	"min": "10:00.0Z",
	"max": "22:00.0Z"
}
```
:::

### Time control
`application/x.meta.control.time+json`

Time input control.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| min           | string  | Minimum input value   | No |
| max 	        | string  | Maximum input value   | No |

:::clear :::

:::sidecode
## Example of datetime control

```json
{
	"@label": "Publish",
	"min": "2016-01-01T15:15:00.111Z",
	"max": "2016-12-01T15:15:00.111Z"
}
```
:::

### Datetime control
`application/x.meta.control.datetime+json`

Date + time input control.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| min           | string  | Minimum input value   | No |
| max 	        | string  | Maximum input value   | No |

:::clear :::