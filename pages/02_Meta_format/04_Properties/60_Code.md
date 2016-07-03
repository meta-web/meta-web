:::sidecode
## Example of Code property

```json
{
	"@type": "meta/properties/text/code",
	"label": "Source",
	"language": "javascript"
}
```
:::

## Code property

**`@type: meta/properties/text/code`** extends **`meta/properties/text`**

Code property represents various source-codes.

Client should support interactive editor and syntax highlighting.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| language | String | Yes | Yes | Code language |

### Supported languages

| ID | Name |
| -- | ---- |
| text | Plain text |
| javascript | JavaScript |
| html | HTML |
| css | CSS |

::: warning
**TO-DO**  
All supported languages should be specified.

IDs may change to mimetypes in the future.
:::