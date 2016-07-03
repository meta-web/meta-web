## Date & time properties

Values must be ISO-8601 compatible or expression.

::: info
**Expression**

Expression is used with `$now` variable and can specify past or future date or time (depends on control type).

`$now-0000-01-00`
`$now+0000-01-00`
`$now`
:::

:::sidecode
## Example of date property

```json
{
	"@type": "meta/properties/date",
	"label": "Date",
	"min": "$now",
	"max": "2016-12-01"
}
```
:::

### Date control

**`@type: meta/properties/date`**

Date property

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| min      | String | No | No | Minimum input value |
| max 	   | String | No | No | Maximum input value |

::: clear :::

:::sidecode
## Example of time property

```json
{
	"@type": "meta/properties/time",
	"label": "Time",
	"min": "10:00.0Z",
	"max": "22:00.0Z"
}
```
:::

### Time control

**`@type: meta/properties/time`**

Time property

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| min      | String | No | No | Minimum input value |
| max 	   | String | No | No | Maximum input value |

::: clear :::

:::sidecode
## Example of datetime property

```json
{
	"@type": "meta/properties/datetime",
	"label": "Start",
	"min": "2016-01-01T15:15:00.111Z",
	"max": "2016-12-01T15:15:00.111Z"
}
```
:::

### Datetime control

**`@type: meta/properties/datetime`**

Datetime property

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| min      | String | No | No | Minimum input value |
| max 	   | String | No | No | Maximum input value |