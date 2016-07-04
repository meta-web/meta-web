## Action response

When client invokes resource's action then response MUST be in JSON format with following properties.

:::sidecode
## customers.php {.tag .post}
```json
{
	"message": "Customer has been created.",
	"navigate": "./38.meta"
}
```
:::

### Sucessfull response

**HTTP code: 2xx**

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| message  | String | No | Response message that should by dispayed to user. Recommended |
| navigate | String / URI | No | If user should be redirected to specified URI |

::: clear :::

:::sidecode
## customers.php {.tag .post}
```json
{
	"message": "Field 'First name' has invalid value.",
	"code": "FIELD_INVALID",
	"field": "first_name"
}
```
:::

### Invalid request

**HTTP code: 4xx**

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| message  | String | Yes | Error message that should by dispayed to user |
| code  | String | No | Internal error code - usable for debugging |

::: info
Additional properties can be returned for more detailed debugging.
:::

::: clear :::

:::sidecode
## customers.php {.tag .post}
```json
{
	"message": "Cannot create customer: internal error occoured",
	"code": "ERR_INTERNAL",
	"debug": "Table 'db.customers' doesn't exist"
}
```
:::

### Error response

**HTTP code: 5xx**

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| message  | String | Yes | Error message that should by dispayed to user |
| code  | String | No | Internal error code - usable for debugging |

::: info
Additional properties can be returned for more detailed debugging.
:::