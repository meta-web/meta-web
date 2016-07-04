## `/tm1.meta`
`application/x.meta+json`

```json
{
	"@doctype": "meta/property",
	"@type": "meta/properties/meter",
	"$data": {
		"@type": "meta/data",
		"uri": "/tm1.json"
	},
	"label": "Living room temperature",
	"min": 0,
	"max": 30,
	"units": "Degress",
	
	"actions": [
		{
			"method": "PUT",
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