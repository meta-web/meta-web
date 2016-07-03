## Server sent events

:::sidecode
**/records.json** {.tag .get}

```
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Content-Type: application/json; charset=UTF-8
Content-Encoding: UTF-8
X-Meta-EventSource: /records.es

{
	"value": 23
}
```

**/records.es** {.tag .get}

```
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Content-Type: text/event-stream
Content-Encoding: UTF-8

data: {
data: "value": 21
data: }
```
:::

MetaWEB controls reads data to model from various data sources. Nowdays live updates of data are becoming essential.

MetaWEB concepts defines way to provide live data updates of resources using [server sent events](https://html.spec.whatwg.org/multipage/comms.html#server-sent-events).

URL of EventSource can be provided using HTTP header **`X-Meta-EventSource`**.

Server then should respond with proper EventSource **without specifing event name**.

See example of EventSource response

:::clear :::