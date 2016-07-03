## Introduction

Most of MetaWEB file types are based on JSON format.

### 2-layer principle

**Concept defines two layers:**
 - Data layer - RAW data files (text, JSON, media files)
 - Meta layer - concept specific formats which describes relations and context of data which leads to information
   - Model (state) - provides access to current state data
   - Configuration - configuration of control
   - Actions - each resource can be actionable

:::sidecode
## Example of model URIs

```json
{
	"@model": "./post/10.json",
	"@model": "http://my.blog.tld/posts/10.json"
}
```

## Using URN to reference local model
```json
{
	"@model": "model:$posts.10"
}
```

## Creating default model

```json
{
	"@model": "#model",
	"@embed": {
		"#model": {
			"@mimeType": "application/json",
			"first_name": "John",
			"last_name": "Doe"
		}
	}
}
```
:::

### Model

Each control and layout works with model which provides data to current scope.

Model can be specified with `@model` property in following formats:

 - URL to data resource
 - URN to local model, eg.: `model:$first_name`
 - URI with data, eg: `data:text/plain,hello%20world`

If model is not specified then local model is set to empty object `{}`.

::: info
To reference local model you can use URN with schema `model` which is object dot notation.

Single dollar sign `$` represents current scope.
Double dollar sign `$` represents top scope if available. Works when model property is passed to child controls.

`model:$`  
`model:$first_name`  
`model:$address.street`
:::

::: warning
**Client-side model providers**

Standard interface should be defined for client-side storages - equivalent to LocalStorage or IndexedDB.
:::

:::clear :::

:::sidecode
## Usage of descriptive properties

```json
{
	"@label": "About MetaWEB",
	"@icon": "./article.svg",
	"@schema": "content.article"
}
```
:::

### Descriptive properties

Every meta resource has following descriptive properties.

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| @label        | string | Title of current resource - should be displayed in user interface | No |
| @icon         | uri    | URI to icon resource which must be image type. | No |
| @schema       | string | Type of resource specified in [Schema vocabulary](../schema-vocabulary/). | No |

:::clear :::

:::sidecode
## Example of actions

```json
{
	"@actions": [
	 	{
	 		"@schema": "UpdateAction",
			"url": "./temperature.json",
			"method": "post",
			"model": "model:$value",
			"label": "Set temperature",
			"icon": "./icons/temperature.svg"
		},
	 	{
			"url": "./temperature.json",
			"method": "put",
			"model": "data:application/json,%7Bvalue%3A0%7D",
			"label": "Turn off",
			"icon": "./icons/off.svg"
		},
	 	{
			"url": "./settings.meta",
			"method": "navigate",
			"label": "Control settings",
			"icon": "./icons/settings.svg"
		}
	]
}
```
:::

### Actions

Every meta resource can be actionable. Actions are specified in `@actions` array property.

Every action has following properties.

| Property name | Type   | Description                                      | Required |
| ------------- | ------ | ------------------------------------------------ | -------- |
| url           | url    | URL to resource where data will be posted. | Yes |
| method        | string | HTTP method to submit data. Default is `POST`. Also `navigate` method is available which redirects user to specified uri. | No |
| model         | urn    | URN to local model of data to be sent. Default is `model:$` | No |
| label         | string | Title of current resource - should be displayed in user interface | Yes |
| icon          | uri    | URI to icon resource which must be image type. | No |
| @schema       | string | Type of action specified in [Schema vocabulary](../schema-vocabulary/). | No |

::: info
**Data format**

 - POST, PUT and DEL methods encodes data as `application/json` and sends them in request body
 - GET method encodes data as query string
:::

:::clear :::

:::sidecode
## Example of embedding meta documents

```json
{
	"@embed": {
		"./counter.meta": {
			"@mimeType": "application/x.meta.control.number+json",
			"@label": "Temperature",
			"@icon": "./icons/temperature.svg",
			"@model": "./counter.json",
			"style": "gauge",
			"min": -50,
			"max": 50,
		}
	}
}
```
:::

### Embedding

Meta file types has many relations to another resource. To lower network requests these relations can be embedded to current document.

Embedded documents must be specified as `@embed` meta property which is object where keys are resource URIs and value is contents of embedded document. Each document record must have `@mimeType` property which specifies embedded document mime type and must be `json` compatible.

:::clear :::