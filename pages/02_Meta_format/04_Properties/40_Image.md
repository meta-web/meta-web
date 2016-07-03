:::sidecode
## Example of Image property

```json
{
	"@type": "meta/properties/image",
	"label": "Avatar",
	"uri": "/avatar.jpg",
	"style": "avatar"
}
```
:::

## Image property

**`@type: meta/properties/image`** extends *`meta/properties/text/uri`*

Image property represented as URI.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| uri   | String / URI | Yes | No | URI to image resource |
| style | String | No | No | How to display image, one of `default`, `cover`, `contain`, `circle`, `avatar`, `icon` |
| vAlign | String | No | No | Vertical image alignment when croped, one of `top`, `center`, `bottom`. Default is `center` |
| hAlign | String | No | No | Horinzotal image alignment when croped, one of `left`, `center`, `right`. Default is `center` |

::: warning
**TO-DO**  
Styles must be described.
:::