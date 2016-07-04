:::sidecode
## Request {.tag .get}

```text
GET collection.php?

where[]["first_name"]="John"&
where[]["last_name"]["@contains"]="Do"&
where[]["role"]["@gt"]=1&
where[]["address.street"]["@match"]=".*Republic$"&
where[]["enabled"]="true"

order["last_name"]="asc"&

start=10&
count=30
```

**Converted to SQL**

```sql
SELECT * FROM customers
WHERE first_name = "John"
AND last_name LIKE "%Do%"
AND role > 1
AND address.street MATCH ".*Republic$"
AND enabled = TRUE
ORDER BY last_name ASC
LIMIT 30 OFFSET 10
```

```text

```

## Request {.tag .get}

```text
GET collection.php?

where[]["@or"][]["first_name"]="John"
where[]["@or"][]["first_name"]="Jack"
where[]["@or"][]["first_name"]["@contains"]="Pete"
where[]["@or"][]["first_name"]["@noteq"]="Emilly"
where[]["enabled"]="true"

```

**Converted to SQL**

```sql
SELECT * FROM customers
WHERE
(
	first_name = "John"
	OR
	first_name = "Jack"
)
AND enabled = TRUE
```

```text

```

## Sample response {.tag .get}

```json
{
	"records": [
		{
			"id": 1,
			"first_name": "John",
			"last_name": "Doe",
			"address": {
				"street": "Rosestreet 42",
				"city": "Sunnyville"
			},
			"role": 1,
			"enabled": true
		},
		{
			"id": 3,
			"first_name": "Jack",
			"last_name": "Jinxster",
			"address": {
				"street": "Lander street 15",
				"city": "Cloudyville"
			},
			"role": 3,
			"enabled": true
		},
		{
			"id": 8,
			"first_name": "Peter",
			"last_name": "Winster",
			"address": {
				"street": "Cold Lane 1",
				"city": "Wintermill"
			},
			"role": 2,
			"enabled": true
		}
	],
	"start": 0,
	"count": 3,
	"total": 368
}
```
:::

## Collection datasource

Model's **`@type: meta/datasource`**

Purpose of datasource type is to provide record data for collection with support of pagination, filtering and ordering.

Request is sent to server via GET method with conditions and result MUST be in JSON format as specified below.

### Request {.tag .get}

Server MUST process following query parameters.

| Parameter | Values | Description |
| --------- | ------ | ----------- |
| `order[<property>]` | `asc` or `desc` | Order records by this column |
| `where[][<key>]` | `<value>` | Filter records by conditions - see below |
| `start` | Integer | Return records starting with position |
| `count` | Integer | Return maximaly specified count of records |

### Response {.tag .get}

```json
{
	"records": [ ... ],
	"start": 10,
	"count": 10,
	"total": 42
}
```

| Property | Type | Description |
| -------- | ---- | ----------- |
| records | Array of Object | Array of records |
| start | Integer | Starting cursor position - as requested |
| count | Integer | Count of returned records |
| total | Integer | Total count of records in collection |

### Filtering conditions

Filter is specified as an array of conditions. Each condition is in format `[key][condition]=value` where value can be another group of conditions.

::: info
Key can be specified as **object notation**, eg.: `address.street`.
:::

| Condition | Value | Description |
| --------- | ----- | ----------- |
| `<property>` | Any | Equals to value |
| `@eq` | Any | Property  equals to value |
| `@noteq` | Any | Property NOT equals to value |
| `@gt` | Number | Property is greater then value |
| `@gte` | Number | Property is greater or equal to value |
| `@lt` | Number | Property is lower then value |
| `@lte` | Number | Property is lower or equal to value |
| `@in` | Number or String | Property (array) contains value |
| `@notin` | Number or String | Property (array) NOT contains value |
| `@match` | String / RegExp | Property matches regular expression specified by value |
| `@notmatch` | String / RegExp | Property NOT matches regular expression specified by value |
| `@contains` | String | Property contains text value |
| `@notcontains` | String | Property NOT contains text value |
| `@or` | Array | Group of conditions with OR comparision |
| `@and` | Array | Group of conditions with AND comparision |

::: warning
Top-level conditions MUST be treaten as AND comparision.
:::

::: success
**Filtering support**  
If some features are not support such as object notation in standard SQL databases then filter model specified in MetaWEB resource file must be one-level or unsupported filter properties MUST NOT be specified in that file.
:::