:::sidecode
## Example of collection records file

```json
{
	"count": 30,
	"records": [
		{
			"@model": "./users/1.json",
			"@ref": "./users/1.meta",
			"first_name": "John",
			"last_name": "Doe",
			"is_vip": false
		},
		{
			"@model": "./users/2.json",
			"@ref": "./users/2.meta",
			"first_name": "Jack",
			"last_name": "Daniels",
			"is_vip": true
		}
	]
}
```
:::

## Collection records {.tag .get}

This file type represents collection records data.

| Feature | Value |
| ------- | ----- |
| Mime-type | `application/x.meta.collection.records+json` |
| Cachable | No |

### Properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| count         | integer | Total count of records in collection | Yes |
| records       | array  | Array of records in collection | Yes |

### Record properties

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| @model        | uri    | URI to record data so it can be accessed without loading of `ref` resource. | No |
| @ref  		| uri    | URI of record layout file that should be navigated as record detail. | No |

:::clear :::