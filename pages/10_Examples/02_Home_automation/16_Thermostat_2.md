## `/tm2.meta`
`application/x.meta.control.number.meter+json`

```json
{
	"@model": "/tm2.json",
	"@label": "Bedroom temperature",
	"min": 0,
	"max": 30,
	"units": "Degress",
	
	"@actions": [
		{
			"url": "/tm2.json",
			"id": "set",
			"label": "Set"
		}
	]
}
```

### `/tm2.json`
`application/json`

```json
{
	"value": 23,
	"state": 22.5
}
```