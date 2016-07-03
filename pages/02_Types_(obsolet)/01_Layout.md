:::sidecode
## Example of layout file

```json
{
	"label": "User profiles",
	"icon": "./icon.svg",
	"style": "grid",
	"controls": [
		{
			"uri": "./header.png",
			"context": "head"
		},
		{
			"uri": "./list.meta",
			"context": "main",
		},
		{
			"uri": "./summary.meta",
			"context": "foot"
		},
		{
			"uri": "./topUsers.meta",
			"context": "aside",
			"group": "1"
		},
		{
			"uri": "./newUsers.meta",
			"context": "aside",
			"group": "2"
		},
		{
			"uri": "./addUser.meta",
			"context": "actions",
			"link": true
		}
	]
}
```
:::

## Layout {.tag .get}

Layout defines list of controls in current scope with meta data.

| Feature | Value |
| ------- | ----- |
| Mime-type | `application/x.meta.layout+json` |
| Cachable | Yes |

### Index properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| @label        | string  | Title of current resource - should be displayed in user interface | No |
| @icon         | string  | Icon (for user interface) - should be URI to SVG file | No |
| @model        | uri     | URI to model resource | No |
| controls     | array   | Array of objects which represents available controls. | Yes |
| style        | string  | Specifies how controls should be displayed. One of ( grid / form ). Default is `grid`. | No |

### Control properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| uri           | uri    | URI of resource. | Yes |
| context       | string | Context of resource - represents information importance and user-interface location. Default is `main`. | No |
| group         | string | Specifies group in given context - eg. 2 aside groups should be displayed as 2 separate sidebars | No |
| link          | boolean | By default control is embeded into current UI view. When link is set to `true` then target control is displayed as link. | No |
| model         | uri | URI to model resource which should be passed to control. Due to security reasons model can be passed only to resources on the same domain. | No |

::: info
**Valid control types** {.title}

Controls can be
 
 - Another meta types
 - HTML documents
 - Media files
 - Other types supported by browser
:::

:::clear :::