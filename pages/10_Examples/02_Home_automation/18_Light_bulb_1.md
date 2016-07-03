## `/lb1.meta`
`application/x.meta.control.boolean+json`

```json
{
	"@model": "/lb1.json",
	"@label": "Living room lights",
	"style": "switch",
	"@actions": [
		{
			"url": "/lb1.json",
			"label": "Set",
			"id": "set"
		},
		{
			"url": "/lb1.json",
			"label": "Turn on",
			"model": "data:application/json,%7Bvalue%3Atrue%7D"
		},
		{
			"url": "/lb1.json",
			"label": "Turn off",
			"model": "data:application/json,%7Bvalue%3Afalse%7D"
		}
	]
}
```

### `/lb1.json`
`application/json`

```json
{
	"value": true
}
```