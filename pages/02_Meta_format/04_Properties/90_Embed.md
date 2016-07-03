:::sidecode
## Example of Embed property

```json
{
	"@type": "meta/properties/embed",
	"label": "Your profile",
	"uri": "../profile.meta",
	"link": true
}
```
:::

## Embed property

**`@type: meta/properties/embed`**

Property which embeds another MetaWEB resource. Property model is passed to child document.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| uri | String / URI | Yes | Yes | URI of embedded MetaWEB resource |
| link | Boolean | No | No | If link to targer resource should be displayed |