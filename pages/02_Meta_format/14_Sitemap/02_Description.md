::: sidecode

## Sitemap example

```json
{
	"@doctype": "meta/sitemap",
	"items": [
		{
			"uri": "./intro.meta",
			"label": "Intro",
			"description": "Introduction to MetaWeb concept.",
			"keywords": [ "metaweb", "web", "future", "introduction" ],
			"icon": "./icons/home.svg"
		},
		{
			"uri": "./concept.meta",
			"label": "Concept",
			"alises": [ "Concepts", "About", "Description" ],
			"icon": "./icons/document.svg",
			"items": [
				{
					"uri": "./concept/principles.meta",
					"label": "Principles"
				},
				{
					"uri": "./concept/architecture.meta",
					"label": "Architecture"
				}
			]
		},
		{
			"uri": "./contact.meta",
			"label": "Contact",
			"icon": "./icons/email.svg"
		}
	]
}
```

:::

## Description

**`@doctype: meta/sitemap`**

Sitemap describes application structure and thus provides navigation tree.

::: info
Client browser should display sitemap as navigation element if available.
:::

### Properties

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| items | Array of Object | Yes | Root navigation items |

### Item properties

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| uri | String / URI | No | URI to item MetaWeb resource |
| label | String | Yes | Item label |
| alises | Array of String | No | Alternative labels |
| description | String | No | Item description |
| keywords | Array of String | No | Item keywords |
| icon | String / URI | No | URI to application's icon, all image formats are supported but SVG is recommended |
| items | Array of Object | No | Child items array |

::: info
When URI is no provided then items should be treaten as title or group.
:::