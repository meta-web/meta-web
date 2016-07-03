:::sidecode
## Example of type `application/x.meta.control.number+json`

```json
{
	"@model": "./temp.json",
	"@label": "Living room",
	"@description": "Temperature of living room.",
	"@hint": "Set temperature of living room.",
	"@visibleIf": "$$.heating",
	"@enabledIf": "$$.heating.enabled == true",
	"@required": true,
	"@readonly": false,
	"min": -50,
	"max": 50
}
```
:::

## Controls {.tag .get}

Controls are specific meta types which are sharing common propeties together with following ones.

### Properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| @description  | string | Description which should be displayed next to a property | No |
| @hint  		| string | Help hint | No |
| @enabledIf  	| string | Condition when control should be enabled | No |
| @visibleIf  	| string | Condition when control should be visible | No |
| @required  	| boolean | If control value must be provided to be valid. Applies only if control is enabled and visible. | No |
| @readonly  	| boolean | If control is readonly | No |

::: warning
**Conditions** {.title}

Condition format must be specified - TO-DO. Conditions will refer to current model.
:::

::: warning
**Bad example** {.title}

Code is not good real scenario example.
:::