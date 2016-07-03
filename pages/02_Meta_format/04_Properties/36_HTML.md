:::sidecode
## Example of HTML property

```json
{
	"@type": "meta/properties/html",
	"label": "Content"
}
```
:::

## HTML property

**`@type: meta/properties/html`**

Property which represents content as HTML.

When not read-only then content should be editable same way as `contenteditable` attribute works in browsers.

::: warning
**Styling and scripts**  
No CSS and scripting is allowed in HTML control.
:::

::: info
It is recommended to format content using semantic tags such as `<strong>` or `<em>`.
:::