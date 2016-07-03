
:::sidecode
## Example of list control

```json
{
	"@label": "Attachments",
	"layout": "./attachment.meta",
	"minItems": 1,
	"maxItems": 10
}
```

## More complex example

```json
{
	"@label": "Compose new e-mail",
	"controls": [
		{
			"uri": "#subject",
			"model": "model:$subject"
		},
		{
			"uri": "#body",
			"model": "model:$body"
		},
		{
			"uri": "#attachments",
			"model": "model:$attachments"
		}
	],
	"@embed": {
		"#subject": {
			"@mimeType": "application/x.meta.control.text+json",
			"@label": "Subject",
			"@required": true
		},
		"#body": {
			"@mimeType": "application/x.meta.control.text+json",
			"@label": "Body",
			"@required": true
			"multiline": true
		},
		"#attachments": {
			"@mimeType": "application/x.meta.control.list+json",
			"@label": "Attachments",
			"@layout": "#attachmentItem"
		},
		"#attachmentItem": {
			"@mimeType": "application/x.meta.layout+json",
			"controls": [
				{
					"uri": "#attachmentFile",
					"model": "model:$file"
				}
			]
		},
		"#attachmentFile": {
			"@mimeType": "application/x.meta.control.file+json",
			"@label": "File"
		}
	},
	"@actions": [
		{
			"url": "./send",
			"@label": "Send e-mail"
		}
	]
}
```
:::

## List control
`application/x.meta.control.list+json`

Control which provides dynamic list of child layouts.

This control requires `layout` to be defined. Child layout model will be added to list as object.

Value of this control is `array`.

Should be displayed with `+` and `-` buttons.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| layout 		| uri     | URI of property list. Must be compatible with mime type: `application/json+meta.properties` | Yes |
| minItems      | integer | Minimum number of items that must be present in list - defaults to `0` | No |
| maxItems      | integer | Maximum number of items that can be present in list. | No |

::: info
**Example usage**

Usable when you need dynamic count of attachments where each attachment consists of another controls.
:::