:::sidecode
## Example of sitemap type

```json
{
	"resources": [
		{
			"url": "./intro.meta",
			"label": "Intro",
			"description": "Introduction to MetaWeb concept.",
			"keywords": [ "metaweb", "web", "future", "introduction" ],
			"icon": "./icons/home.svg"
		},
		{
			"url": "./concept.meta",
			"label": "Concept",
			"icon": "./icons/document.svg",
			"resources": [
				{ "url": "./concept/principles.meta" },
				{ "url": "./concept/architecture.meta" }
			]
		},
		{
			"url": "./contact.meta",
			"label": "Contact",
			"icon": "./icons/email.svg"
		}
	]
}
```
:::

## Sitemap {.tag .get}

This file type represents navigation tree of site or application.

| Feature | Value |
| ------- | ----- |
| Mime-type | `application/x.meta.sitemap+json` |
| Cachable | Yes |

### Properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| resources     | array  | Array of available resources                     | Yes |

### Resource properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| url           | url    | URL of resource. | Yes |
| label         | string | Label of resource. | No |
| description   | string | Description of resource. | No |
| icon          | uri    | URI to icon. Icon should be an image. | No |
| keywords      | array  | Descriptive keywords specified as array of strings. | No |
| resources     | array  | Array of child resources. | No |

:::clear :::

:::sidecode
## Example of HTTP response

```
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Content-Type: application/x.meta.layout+json; charset=UTF-8
Content-Encoding: UTF-8
X-Meta-Sitemap: /sitemap.meta
```
:::

### HTTP header reference

Sitemap can be navigated directly or can be referenced from other resources using special HTTP header.

`X-Meta-Sitemap: /sitemap.meta`