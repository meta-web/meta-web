## `/tm2.meta`
`application/x.meta+json`

```json
{
	"@doctype": "meta/property",
	"@type": "meta/properties/meter",
	"$data": {
		"@type": "meta/data",
		"uri": "/tm1.json"
	},
	"label": "Bedroom temperature",
	"min": 0,
	"max": 30,
	"units": "Degress",
	
	"actions": [
		{
			"method": "PUT",
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
	"value": 22,
	"state": 23.0
}
```