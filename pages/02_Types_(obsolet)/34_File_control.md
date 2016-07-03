
:::sidecode
## Example of file control

```json
{
	"@label": "Profile image",
	"mimeType": "image\/*",
	"maxSize": 10000000
}
```
:::

## File control
`application/x.meta.control.file+json`

File control.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| mimeType 		| string  | RegExp of allowed file mime types. | No |
| maxSize       | integer | Maximum allowed size of file in bytes. | No |

::: info
**Multiple files** {.title}

Multiple files (array) can be implemented using `list` control.
:::