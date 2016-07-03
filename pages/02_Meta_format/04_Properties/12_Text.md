:::sidecode
## Example of text property

```json
{
	"@type": "meta/properties/text",
	"label": "Username",
	"minLength": 5,
	"maxLength": 32,
	"pattern": "^[a-zA-Z0-9]+$",
	"multiline": true
}
```
:::

## Text property

**`@type: meta/properties/text`**

Basic text input

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| minLength | Integer | No | No | Minimum input length |
| maxLength | Integer | No | No | Maximum input length |
| pattern  	| String  | No | No | Validation RegExp |
| multiline | Boolean | No | No | If control is multiline and should be displayed as textarea |