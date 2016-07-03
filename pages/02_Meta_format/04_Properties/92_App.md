:::sidecode
## Example of App property

```json
{
	"@type": "meta/properties/map",
	"label": "3D view",
	"uri": "./viewer.html"
}
```
:::

## App property

**`@type: meta/properties/app`**

App property represents full-featured HTML5 application which is displayed as `iframe`.

All HTML, CSS and scripting features must be supported.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| uri | String / URI | Yes | Yes | URI to application main HTML file |

::: warning
**Usage**  
This property should be used only in extrem cases when special functionality is needed because application runs out of MetaWEB platform so it is not parsable and does not provide MetaWEB benefits.
:::