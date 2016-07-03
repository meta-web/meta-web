:::sidecode
## Example

```json
{
	"@doctype": "meta/resource",
	...
	"parent": "../index.meta",
	"previous": "./41.meta",
	"next": "./43.meta",
	"sitemap": "/sitemap.meta",
	"manifest": "/manifest.meta"
}
```
:::

## Navigation properties

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| parent | String / URI | No | Yes | URI to parent resource |
| previous | String / URI | No | Yes | URI to previous resource on same navigation level |
| next | String / URI | No | Yes | URI to next resource on same navigation level |
| sitemap | String / URI | No | Yes | URI to MetaWEB sitemap file |
| manifest | String / URI | No | Yes | URI to MetaWEB application manifest file |