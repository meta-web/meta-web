
## Authentication

**Authentication flow:**

1) Client tries to access protected resource.
2) Server must respond to resource request with **HTTP 401** status code with meta-data as response body.
3) Client choses auth method:
	1) If `navigate` then client must navigate to specified URI
	2) If `identity` then client sends auth request to identity server and then calls specified resource server URI with access token and identity server URL - see Central identity concept. This process should be processed in background without renavigating.
4) If client authenticates then resource server must respond with successfull action response with `token` property.
5) Client now tries to access protected resource with token set as `X-Meta-Token` request HTTP header.

:::sidecode
## protected.meta {.tag .get}
```text
HTTP/1.1 401 Unauthorized
Content-type: application/x.meta+json
...
```

```json
{
	"@doctype": "meta/protected",
	"providers": [
		{
			"type": "navigate",
			"label": "Log in via Facebook",
			"uri": "https://www.facebook.com/dialog/oauth?client_id=xxx&redirect_uri=https%3A%2F%2Fmymetaserver%2Flogin.meta"
		},
		{
			"type": "identity",
			"scope": [ "contact", "email", "avatar" ],
			"uri": "http://mymetaserver.com/auth"
		}
	]
}
```
:::

### 401 Unauthorized response

Response body is JSON encoded MetaWeb document with follwing properties.

| Property | Type | * | Description |
| -------- | ---- | - | ----------- | 
| @doctype | String | Yes | `meta/protected` |
| providers | Array of Object | Yes | List of available auth providers |

**Provider properties**

| Property | Type | * | Description |
| -------- | ---- | - | ----------- | 
| type | String | Yes | Provider type, one of: `navigate`, `identity` (central identity concept) |
| label | String | Yes if `navigate` provider | Provider label, eg.: Facebook, Google, Twitter, Internal |
| uri | String / URI | Yes| URI to MetaWeb document where client can authenticate |
| scope | Array of String | Yes if `identity` provider | Required data from identity server |

::: clear :::

:::sidecode
## Request auth.php
```json
{
	"@doctype": "meta/response/auth",
	"token": "abc123",
	"path": "/myweb/",
	"expires": "2016-12-01T15:15:00.111Z"
}
```
:::

### Authentication response

When client tries to authenticate then server must respond with [MetaWeb action response](../../meta-format/api/#10_Action_response).

If unsucessfull then standard error response is sent.

**When successfull** then server must provider `token` property in response and `meta/response/auth` doctype.

**Successfull response properties:**

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| @doctype | String | Yes | `meta/response/auth` | 
| token | String | Yes | Authorization token which will be used to request protected resources |
| path | String | No | Auth token is applicable only on specified path |
| expires | String | No | ISO-8601 formated date and time when token expires |

Client remembers this token for session and uses it to request protected resources.

::: clear :::

:::sidecode
## protected.meta {.tag .get}
```text
GET /protected.meta
X-Meta-Token: abc123
...


HTTP/1.1 200 OK
...
```

```json
{
	"@doctype": "meta/resource",
	...
}
```
:::

### Protected resource request

Then when client tries to access protected resource it sends `token` as `X-Meta-Token` HTTP header.