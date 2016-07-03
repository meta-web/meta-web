## `/tm1.meta`
`application/x.meta.control.number.meter+json`

```json
{
	"@model": "/tm1.json",
	"@label": "Living room temperature",
	"min": 0,
	"max": 30,
	"units": "Degress",
	
	"@actions": [
		{
			"url": "/tm1.json",
			"id": "set",
			"label": "Set"
		}
	]
}
```

### `/tm1.json`
`application/json`

```json
{
	"value": 23,
	"state": 22.5
}
```