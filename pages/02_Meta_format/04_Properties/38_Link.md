:::sidecode
## Example of Link property

```json
{
	"@type": "meta/properties/text/link",
	"label": "Source",
	"select": "http://www.identity.meta/profiles/index.meta",
	"pattern": "^http:\/\/www.identity.meta\/profiles\/*$"
}
```
:::

## Link property

**`@type: meta/properties/text/link`** extends **`meta/properties/uri`**

Link property represents link to existing MetaWEB resource.

Can be displayed as text input or as selector of available resources.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| select   | String / URI | No | Yes | URI to MetaWEB resource which can be used as menu. Target resource MUST implement action with `@select` schema ID |

::: warning
**Validation**  
Client must validate selected resource by trying to load it. Then it can display it's item and icon.
:::

::: info
**Multiple links** {.title}

Multiple links (array) can be implemented using `meta/properties/list` control.
:::