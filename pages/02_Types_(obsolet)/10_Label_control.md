:::sidecode
## Example of label control

```json
{
	"@label": "Greetings",
	"contents: "Hello {{name}}!"
}
```
:::

## Label control
`application/x.meta.control.label+json`

Control that only shows specified contents.

| Property name | Type   | Description           | Required |
| ------------- | ------ | --------------------- | -------- |
| contents  	| string  | Label contents       | Yes |

::: info
**Variables**

Variables can be referenced using handlerbar notation.
:::