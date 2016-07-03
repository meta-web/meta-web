:::sidecode
## Basic MetaWEB file

```json
{
	"@doctype": "meta/resource"
	...
}
```

## Vendor specific type

```json
{
	"@doctype": "cz.cryonix/net/dummy"
	...
}
```
:::

## Overview

MetaWEB files are written in [JSON format](https://en.wikipedia.org/wiki/JSON) and has mime type **`application/x.meta+json`**.

Every Meta file must has document type specified as **`@doctype`** property.

MetaWEB is meant to be extensible so every standard type is prefixed by `meta/` string.

Extended types should be in format `<vendor>/[package/]<type>`.

::: warning
Vendor specific types should be used only in extreme cases where custom software extension is needed and there is no standard way how to achive desired functionality.
:::