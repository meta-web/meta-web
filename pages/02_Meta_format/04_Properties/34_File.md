:::sidecode
## Example of file property

```json
{
	"@type": "meta/properties/file",
	"label": "Profile picture",
	"mimeType: "image/*",
	"maxSize": 1000000
}
```
:::

## File property

**`@type: meta/properties/file`**

Property which enabled to upload file and provides link to current file if set.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| mimeType | String | No | No | RegExp of allowed file mime types |
| maxSize  | Integer | No | No | Maximum allowed size of file in bytes |

::: info
**Multiple files**  
Multiple files (array) can be implemented using `meta/properties/list` type.
:::

### Model & encoding

File property model is object and has following structure:

| Property | Type | Description |
| -------- | ---- | ----------- |
| filename | String | Filename |
| mimeType  | String | File mimetype |
| size | Integer | File size in bytes |
| uri | String | Uri to current file |

::: info
Filename, mimetype and size is provided when new file is selected.

When loading remote model it's recommended to provide URI property which references to current uploaded file if possible. Server also can provide filename, mimetype and size too.
:::

::: warning
**Encoding**

File contents is sent to server as **`base64`**.
:::