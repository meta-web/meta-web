## `/lb1.meta`
`application/x.meta+json`

```json
{
	"@doctype": "meta/property",
	"@type": "meta/properties/boolean",
	"$data": {
		"@type": "meta/data",
		"uri": "/lb1.json"
	},
	"$on": {
		"@type": "meta/data",
		"value": true
	},
	"$off": {
		"@type": "meta/data",
		"value": true
	},
	"model": "$data",
	"label": "Living room lights",
	"style": "switch",
	"min": 0,
	"max": 30,
	"units": "Degress",
	
	"actions": [
		{
			"method": "PUT",
			"url": "/tm1.json",
			"model": "$data",
			"id": "set",
			"label": "Set",
		},
		{
			"method": "PUT",
			"url": "/tm1.json",
			"model": "$on",
			"label": "Turn on",
			"aliases": [ "Switch on", "Light on" ]
		},
		{
			"method": "PUT",
			"url": "/tm1.json",
			"model": "$off",
			"label": "Turn off",
			"aliases": [ "Switch off", "Light off" ]
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