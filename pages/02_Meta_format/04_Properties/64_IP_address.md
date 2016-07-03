## IP address properties

Various properties which are representing IPv4 and IPv6 addresses and masks.

:::sidecode
## Example of IPv4 address property

```json
{
	"@type": "meta/properties/ipv4/address",
	"label": "IP address",
	"subnet": "192.168.0.0",
	"mask": 24
}
```
:::

### IP address

**`@type: meta/properties/ipv4/address`**  
**`@type: meta/properties/ipv6/address`**

IPv4 and IPv6 address.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| subnet   | String | No | No | IP address of allowed subnet |
| mask     | Integer | Yes if `subnet` specified | No | Count of mask bits for subnet validation |

::: clear :::

:::sidecode
## Example of IPv4 mask property

```json
{
	"@type": "meta/properties/ipv4/mask",
	"label": "Subnet mask",
	"minBits": 16,
	"maxBits": 24
}
```
:::

### IP mask

**`@type: meta/properties/ipv4/mask`**  
**`@type: meta/properties/ipv6/mask`**

IPv4 and IPv6 mask.

| Property | Type | * | # | Description |
| -------- | ---- | - | - | ----------- |
| minBits  | Integer | No | No | Minimal mask bit count |
| maxBits  | Integer | No | No | Maximal mask bit count |