:::sidecode
## Example of text control

```json
{
	"@label": "Username",
	"minLength": 5,
	"maxLength": 32,
	"pattern": "^[a-zA-Z0-9]+$",
	"multiline": true
}
```
:::

## Text control

`application/x.meta.control.text+json`

Basic text input control

| Property name | Type   | Description           | Required |
| ------------- | ------ | --------------------- | -------- |
| minLength     | integer | Minimum input length | No |
| maxLength 	| integer | Maximum input length | No |
| pattern  		| string  | Validation RegExp     | No |
| multiline  	| string  | If control is multiline and should be displayed as textarea | No |