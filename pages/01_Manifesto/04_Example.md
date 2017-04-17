## Example of META API and META UI

I would like to describe basic idea of using META API and META UI for better concept understanding.

::: warning
This is just an example, concept is under active development and is changing rapidly.
:::

Following demo is based on an address book example.

## Web service - using META API

Our web service has two endpoints which are providing:

1. Collection of contacts
2. Individual contact

**META API is based on OOP principle.** So every endpoint is an object with properties and methods.

- Calling `GET` method will return object properties with values.
- Calling `PUT` method will set object property values or will call method with arguments
- Calling `DELETE` method will delete resource if supported
- Calling `OPTIONS` method will return resource schema (META API description)

But methods described in schema are different than HTTP words. They are describing different resource capabilities:

- Method `GET` means that resource properties can be retrieved (e.g. methods cannot be getted)
- Method `SET` means that resource properties can be updated (or method can be called)
- Method `DELETE` means that resource can be deleted
- Method `LIVE` means that client can subscribe to changes using server sent events (EventSource) - optional feature
- Method `LOCK` means that client can lock record so no one else can modify it - optional feature

### /contacts {.tag .options}

Calling `OPTIONS` HTTP method on `/contacts` endpoint will return resource schema which describes resource model and capabilities.

```text
HTTP response:

Content-type: application/json+x.metaapi
```

```json
{
    "@doctype": "@meta.schema.object",
    "@implements": "@meta.collection",
    "methods": ["GET", "LIVE"],
    "title": "Contacts",
    "properties": {
        "records": {
            "type": "@meta.list.object",
            "label": "Contacts",
            "readonly": true,
            "properties": {
                "id": {
                    "type": "@meta.integer",
                    "label": "Record ID",
                    "private": true,
                    "..comment..": "Private tells UI to not display this field by default."
                },
                "first_name": {
                    "type": "@meta.text",
                    "label": "First name"
                },
                "last_name": "...",
                "email": {
                    "type": "@meta.text.email",
                    "label": "E-mail"
            	}
            }
        },
        "count": {
            "type": "@meta.integer",
            "label": "Total count",
            "readonly": true
        },
        "..comment..": "These properties can be accessed within same resource as this schema using GET, PUT or PATCH methods. In this case of collection only GET method is supported."
    },
    "query": {
        "first_name": {
            "type": "@meta.text",
            "label": "First name"
        },
        "last_name": "...",
        "..comment..": "Specifies query variables that can be used to filter returned properties."
    },
    "relations": {
        "{records.id}": {
            "label": "Record detail"
        },
        "..comment..": "Specifies URI of related endpoints."
    },
    "actions": {
        "create": {
            "label": "Create new contact",
            "..comment..": "Method arguments (properties) can be retrieved by fetching schema for method URI."
        },
        "sendNewsletter": {
            "label": "Send newsletter to contacts"
        }
    }
}
```

### /contacts?offset=10&limit=2 {.tag .get}

Calling `GET` HTTP method on `/contacts` endpoint will return list of contacts.

Because this resource implements `collection` interface we know that we can also filter result and use pagination.

```text
HTTP response:

Content-type: application/json+x.metaapi
```

```json
{
	"@doctype": "@meta.data",
	"@implements": "@meta.collection",
	"records": [
		{ "id": 1, "first_name": "John", "last_name": "Doe", "email": "john@doe.tld" },
		{ "id": 2, "first_name": "Jack", "last_name": "Doe", "email": "jack@doe.tld" }
	],
	"offset": 10,
	"count": 42
}
```

### /contacts$create {.tag .options}

Calling `OPTIONS` HTTP method on `/contacts$create` endpoint will return schema of `create` method of `/contacts` resource.

```text
HTTP response:

Content-type: application/json+x.metaapi
```

```json
{
    "@doctype": "@meta.schema.method",
    "title": "Create contact",
    "methods": ["SET"],
    "properties": {
        "first_name": {
            "type": "@meta.text",
            "label": "First name",
            "required": true
        },
        "last_name": "...",
        "email": {
            "type": "@meta.text.email",
            "label": "E-mail",
            "required": true,
            "hint": "Enter a valid e-mail address."
        },
        "..comment..": "These properties are method arguments. Method endpoint acts as separated data model."
    }
}
```

### /contacts$create {.tag .put}

Calling `PUT` HTTP method on `/contacts$create` endpoint will create a new contact record.

```text
HTTP request body:

{
	"first_name": "Jiri",
	"last_name": "Hybek",
	"email": "jiri@hybek.cz"
}

HTTP response:

200 OK
Content-type: application/json+x.metaapi
```

```json
{
    "@doctype": "@meta.response",
    "type": "success",
    "message": "Contact has been successfully created.",
    "data": {
    	"id": "42",
		"first_name": "Jiri",
		"last_name": "Hybek",
		"email": "jiri@hybek.cz"
    }
}
```

### /contacts/42 {.tag .options}

Calling `OPTIONS` HTTP method on `/contacts/42` endpoint will return record schema. It is important to be able to retrieve schema for every resource because we can have free data structure for records in many cases.

```text
HTTP response:

Content-type: application/json+x.metaapi
```

```json
{
    "@doctype": "@meta.schema.object",
    "methods": ["GET", "SET", "DELETE", "LIVE", "LOCK"],
    "title": "Contacts",
    "properties": {
        "id": {
            "type": "@meta.integer",
            "label": "Record ID",
            "private": true
        },
        "first_name": {
            "type": "@meta.text",
            "label": "First name"
        },
        "last_name": "...",
        "email": "..."
    }
}
```

### /contacts/42 {.tag .get}

Calling `GET` HTTP method on `/contacts/42` endpoint will return record data.

```text
HTTP response:

Content-type: application/json+x.metaapi
```

```json
{
	"@doctype": "@meta.data",
	"id": 42,
	"first_name": "Jiri",
	"last_name": "Hybek",
	"email": "jiri@hybek.cz"
}
```

### /contacts/42 {.tag .put}

Calling `PUT` HTTP method on `/contacts/42` endpoint will update our contact.

```text
HTTP request body:

{
	"first_name": "Jiri",
	"last_name": "Hybek",
	"email": "jiri@hybek.tld"
}

HTTP response:

200 OK
Content-type: application/json+x.metaapi
```

```json
{
    "@doctype": "@meta.response",
    "type": "success",
    "message": "Contact has been successfully saved.",
    "data": {
    	"id": "42",
		"first_name": "Jiri",
		"last_name": "Hybek",
		"email": "jiri@hybek.cz"
    }
}
```

And so on...

## User interface - using META UI

META UI is using XML because it provides great solution for component model.

### /list.meta {.tag .get}

First example is META UI view of contacts collection.

We define our data source, list component which is connected to that datasource and some other information.

We can also optionally specify layout of each record and which fields should be displayed.

Note `export` attribute which tells client that selected record should be available to another views - see more below.

```text
HTTP response:

Content-type: application/xml+metaui
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<meta-ui>
	<link rel="nav" src="/nav.meta" />
	<datasource id="collection" src="/contacts" />
	<collection datasource="@collection" filters="true" export="selection:$selection">
		<layout-columns>
			<column>
				<icon src="/media/contact.svg" size="small" />
			</column>
			<column grow>
				<property name="first_name" label="Jméno" />
				<property name="last_name" /><!-- label is automatically gathered from data source -->
				<link rel="detail" src="/detail.meta?id=#{id}" /> <!-- interpolation passes 'id' property to URL -->
			</column>
		</layout-columns>
	</collection>
</meta-ui>
```

### /contact.meta {.tag .get}

This META UI view displays contact detail.

If resource supports 'SET' method then properties should be displayed as form fields with `Save` button.

Properties can be placed automatically based on data model or we can specify their placement manually.

```text
HTTP response:

Content-type: application/xml+metaui
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<meta-ui>
	<link rel="nav" src="/nav.meta" />
	<!-- data source url accepts query argument 'id' -->
	<datasource id="record" src="/contacts/${id}" />
	
	<!-- all properties are rendered automaticaly based on a data source -->
	<properties datasource="@record" />

	<!-- or we can place properties manually -->
	<group title="Personal">
		<property name="@record.first_name" />
		<property name="@record.last_name" />
	</group>
	<group title="Contact" scope="@record">
		<property name="email" />
	</group>
</meta-ui>
```

### /index.meta {.tag .get}

Our index page -  META UI view that combines previous views into friendly interface with contact list on a left side and with a contact detail on other side. We can achieve this behaviour by using embedding of another META UI views.

Note that we are using exported selection variable from `list.meta` views.

```text
HTTP response:

Content-type: application/xml+metaui
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<meta-ui>
	<link rel="nav" src="/nav.meta" />
	<layout-sidebar>
		<aside>
			<embed src="/list.meta" id="list" />
		</aside>
		<main>
			<embed src="/detail.meta?id=#{@list.selection.id}" />
			<!-- id is gathered from embedded 'list' view which exports it -->
		</main>
	</sidebar>
</meta-ui>
```

### /index.meta {.tag .get}

Finally we define special META UI document called navigation manifest which describes navigation structure of our application. Client is then capable of displaying our navigation.

Note that this navigation manifest was referenced in previous views.

```text
HTTP response:

Content-type: application/xml+metaui
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<meta-nav>
	<title>My app</title>
	<link src="/index.meta" label="Address book" icon="/media/addressbook.svg">
		<!-- child item, client can fetch title automatically -->
		<link src="/list.meta" />
	</link>
</meta-nav>
```

### How to display META UI?

To display META UI views we would need special web browser or client application.

In the future if concept will be popular then I suppose that community can create production browser. Even better solution would be if current web browsers will be able to implement META Web.

In a meantime we would like to develop META Web browser using current web technologies.