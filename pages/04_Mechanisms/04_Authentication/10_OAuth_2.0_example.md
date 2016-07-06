## OAuth 2.0 example

MetaWeb naturaly supports OAuth 2.0 auth with following workflow:

**1) Server responds with 401 HTTP code and meta-data and specifies OAuth server auth URL.**

```text
GET /protected.meta
...
---

HTTP/1.1 401 Unauthorized
Content-type: application/x.meta+json

{
	"@doctype": "meta/protected",
	"providers": [
		{
			"type": "navigate",
			"label": "Login via OAuth server",
			"uri": "http://oauth.server/auth?client_id=xyz&scope=contact&redirect_uri=http%3A%2F%2Fresource.server%2Fauth"
		}
	]
}
```

**2) Client choses `navigate` provider and navigates to OAuth URL.**

**3) OAuth server responds with MetaWeb document which describes UI/mechanisms to log in and authorize request.**

```text
GET http://oauth.server/auth
...
---

HTTP/1.1 200 OK
Content-type: application/x.meta+json

{
	"@doctype": "meta/resource",
	"label": "Authorize aplication Resource server",
	"$req": {
		"@type": "meta/data",
		"value": {
			"client_id": "xyz",
			"scope": [ "contact" ],
			"redirect_uri": "http://resource.server/auth"
		}
	},
	"properties": [ ... ],
	"actions": [
        {
            "method": "POST",
            "uri": "./confirm",
            "model": $req,
            "label": "Authorize"
        }
	]
}
```

**4) Client invokes auth action on login resource and server responds with `navigate` property which is set to callback URL.**

```text
POST http://oauth.server/confirm
Content-type: application/json
...

{
	"client_id": "xyz",
	"scope": [ "contact" ],
	"redirect_uri": "http://resource.server/auth"	
}
---

HTTP/1.1 200 OK
Content-type: application/x.meta+json

{
	"@doctype": "meta/response",
	"navigate": "http://resource.server/auth?token=abc123"
}
```

**5) Client navigates to callback URL.**

**6) Resource server responds on callback URL with `meta/response/auth` and `token` specified.**

```text
GET http://resource.server/auth?token=abc123
...
---

HTTP/1.1 200 OK
Content-type: application/x.meta+json

{
	"@doctype": "meta/response/auth",
	"token": "xyz456"
}
```

7) Client now can access resource with MetaWeb token.

```text
GET http://resource.server/protected.meta
...
---

HTTP/1.1 200 OK
Content-type: application/x.meta+json

{
	"@doctype": "meta/resource",
	"label": "Protected resource",
	...
}
```