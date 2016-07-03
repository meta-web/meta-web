## IP address controls

:::sidecode
## Example of IPv4 control

```json
{
	"@control": "meta.ipv4",
	"@label": "IP address",
	"subnet": "192.168.0.0",
	"mask": 8
}
```
:::

### IPv4 control

Control with IPv4 validation.

| Property name | Type    | Description           | Required |
| ------------- | ------- | --------------------- | -------- |
| subnet 		| string  | IP address of allowed subnet | No |
| mask          | integer | Count of mask bits for subnet validation | Yes if `subnet` specified. |

:::clear :::

::: warning
**TO-DO** {.title}

IPv4, IPv6 and MAC address controls.
:::