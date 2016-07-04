## `/overview.meta`
`application/x.meta+json`

```json
{
	"@doctype": "meta/resource",
	"label": "Overview",
	"icon": "/icons/dashboard.svg",
	"image": "/images/header.jpg",
	"properties": [
		{
			"@type": "meta/group",
			"label": "Thermostats",
			"properties": [
				{
					"@type": "meta/embed",
					"uri": "/tm1.meta",
					"link": true
				},
				{
					"@type": "meta/embed",
					"uri": "/tm2.meta",
					"link": true
				}
			]
		},
		{
			"@type": "meta/group",
			"label": "Lights",
			"properties": [
				{
					"@type": "meta/embed",
					"uri": "/lb1.meta",
					"link": true
				}
			]
		}
	]
}
```