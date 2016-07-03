## Devices (IoT)

:::sidecode
## Examples
```text
device@turnOn
device.thermostat@turnOff
device.light@turnOn
```
:::

### Actions

| Schema ID | Description |
| --------- | ----------- |
| [object]@turnOn | Expresses that device will be turned on. |
| [object]@turnOff | Expresses that device will be turned off. |

:::clear :::

### Objects

| Schema ID | Description |
| --------- | ----------- |
| device | Generic device. |
| device.phone | Generic phone device. |
| device.light | Light device, eg. lightbulb. |
| device.thermostat | Thermostat device. |
| device.lock | Lock device. |
| device.sensor | Generic sensor device |
| device.sensor.camera | Camera sensor device. |
| device.sensor.microphone | Microphone device. |
| device.sensor.speaker | Speaker device. |
| device.sensor.smokeDetector | Smoke detector device. |
| device.network | Generic network device. |
| device.network.router | Network router device. |
| device.network.switch | Network switch device. |
| device.network.port | Network device generic port. |
| device.network.port.ethernet | Network device ethernet port. |
| device.network.port.wireless | Network device wireless port. |

:::clear :::