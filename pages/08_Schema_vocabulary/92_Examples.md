## Examples

### MikroTIK Router

/devices/router.meta {.tag .get}

`application/x.meta.layout+json`

```json
{
	"@label": "MikroTIK RB 433",
	"@icon": "./icons/mikrotik.png",
	"@schema": "device.network.router+vendor.com.mikrotik",
	"@model": "./router.json",
	"controls": [
		{
			"uri": "./port1.meta",
			"group": "Ports"
		},
		{
			"uri": "./port2.meta",
			"group": "Ports"
		},
		{
			"uri": "./port3.meta",
			"group": "Ports"
		},
		{
			"uri": "./port4.meta",
			"group": "Ports"
		}
	],
	"@actions": [
		{
			"url": "./shutDown",
			"label": "Shut down",
			"@schema": "@turnOff"
		}
	]
}
```

/devices/router/portX.meta {.tag .get}

`application/x.meta.layout+json`

```json
{
	"@label": "etherX",
	"@icon": "./icons/port.png",
	"@schema": "device.network.port.ethernet",
	"@model": "./portX.json",
	"controls": [
		{
			"uri": "./counter.meta",
			"model": "model:traffic.rx"
		},
		{
			"uri": "./counter.meta",
			"model": "model:traffic.tx"
		},
		{
			"uri": "./ip.meta",
			"model": "model:config.ip_address"
		},
	],
	"@actions": [
		{
			"url": "./disable",
			"label": "Disable",
			"@schema": "@turnOff"
		},
		{
			"url": "./enable",
			"label": "Enable",
			"@schema": "@turnOn"
		}
	]
}
```