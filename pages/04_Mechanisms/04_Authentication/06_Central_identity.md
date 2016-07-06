## Central identity concept

Central identity concept is based on an idea to have identity server where users have their accounts.

3rd party applications can then access identity information and use these services as log in mechanisms.

Difference between OpenID and other services is that central identity server DOES NOT require application to be known and authorized. It's because following workflow.

**When resource server requires authentication:**

1) Server says that is supports MetaWeb identity mechanism
2) Client contacts identity server and request auth token for resource server
3) Client then passes auth token and identity server URL to resource server
4) Resource server requests identity information from identity server using that token
5) Resource server internaly authenticates client and returns session token as described above

### Identity server API

User registration and log in mechanisms to identity server are up to that server. But when successfully logged in then server MUST respond with proper action response so client can easily recognize properties required for future requests.

:::sidecode
https://identity.server/auth {.tag .post}
```json
{
	"@doctype": "meta/response/auth/identity",
	"token": "abc123",
	"request_uri": "https://identity.server/service_request",
	"profile_uri": "https://identity.server/profile"
}
```
:::

#### Identity server successfull login response

Response MUST be in MetaWeb `meta/response/auth/identity` format, extends `meta/response/auth`.

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| @doctype | String | Yes | `meta/response/auth/identity` | 
| token | String | Yes | Authorization token which will be used to request identity server |
| path | String | No | Auth token is applicable only on specified path |
| expires | String | No | ISO-8601 formated date and time when token expires |
| request_uri | String | Yes | URI where client can request authorzation for resource server |
| profile_uri | String | Yes | URI where client can find his profile |

::: clear

::: sidecode
## https://identity.server/service_request {.tag .post}
```text
POST /service_request
X-Meta-Token: abc123
...
```

```json
{
	"resource": "https://resource.server/protected.meta",
	"scope": [ "contact", "email" ]
}
```

**Response**

```json
{
	"@doctype": "meta/response/identity/token",
	"token": "xyz456",
	"expires": "2016-12-01T15:15:00.111Z",
	"auth_uri": "https://identity.server/service_auth"
}
```
:::

#### Request resource server authorization {.tag .post}

When resource server requires identity authentication then client sends following request to identity server which returns token for that resource server using POST method.

Request is JSON encoded and MUST has following properties.

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| resource | String | Yes | URI of protected resource | 
| scope | Array of String | Yes | Array of required information scope |

::: warning
Client needs to be authenticated to identity server to send this request. So request must be send with `X-Meta-Token` HTTP header.
:::

Identity server then responds with `meta/response/identity/token` type with following properties.

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| @doctype | String | Yes | `meta/response/identity/token` |
| token | String | Yes | Authorization token which will be passed to resource server |
| expires | String | No | ISO-8601 formated date and time when token expires |
| auth_uri | String / URL | Yes | URL where resource server can request identity information |

::: clear :::

::: sidecode
## https://resource.server/auth {.tag .post}
```text
POST /auth
...
```

```json
{
	"token": "xyz456",
	"expires": "2016-12-01T15:15:00.111Z",
	"auth_uri": "https://identity.server/service_auth"
}
```
```
:::

#### Passing token to resource server {.tag .post}

Then client sends access token with identity server URI to resource server using POST method.

Request is sent to URI specified in resource server unauthorized response.

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| token | String | Yes | Authorization token which will be passed to resource server |
| expires | String | No | ISO-8601 formated date and time when token expires |
| auth_uri | String / URL | Yes | URL where resource server can request identity information |

::: clear :::

::: sidecode
## https://identity.server/service_auth {.tag .post}
```text
POST /auth
...
```

```json
{
	"resource": "https://resource.server/protected.meta",
	"token": "xyz456"
}
```

**Response**

```json
{
	"@doctype": "meta/response/identity/profile",
	"first_name": "John",
	"last_name": "Doe",
	"email": "john@doe.tld"
}
```

:::

### Resource server identity request {.tag .post}

Resource server then can request identity data from identity server.

Request is send to specified `auth_uri` using POST method with following properties.

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| resource | String | Yes | Protected resource URI |
| token | String | Yes | Authorization token optained from client |

::: warning
Identity server should check if `resource` URI match with client request.
:::

When successfull then identity server responds with `meta/response/identity/profile` type which has following properties and extends `meta/identity/profile` type.

| Property | Type | * | Description |
| -------- | ---- | - | ----------- |
| @doctype | String | Yes | `meta/response/identity/profile` |
| `<profile>` | - | Yes | Profile data as `meta/identity/profile` type |

Then resource server authenticates client internaly and sends him access token as described above.

### Identity profile

**`@doctype: meta/identity/profile`**

::: warning
TO-DO
:::