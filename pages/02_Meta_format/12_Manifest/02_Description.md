::: sidecode

## Manifest example

```json
{
	"@doctype": "meta/manifest",
	"title": "My app",
	"description": "Description of my cool application.",
	"icon": "/assets/app.svg",
	"author": "John Doe",
	"sitemap": "/sitemap.meta"
}
```

:::

## Description

**`@doctype: meta/manifest`**

Manifest is MetaWEB document in JSON format which describes basic application properties.

### Properties

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| title | String | Yes | Application's title |
| description | String | No | Application's description |
| icon | String / URI | No | URI to application's icon, all image formats are supported but SVG is recommended |
| author | String | No | Application's author |
| sitemap | String / URI | No | URI to application sitemap |