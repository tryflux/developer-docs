# Authentication

Authentication is via the client credentials grant of the OAuth 2 specification.  
1. Retrieve a valid `access_token` using the [Token](#token) resource
2. Include this token using the Bearer scheme in all future requests using the `Authorization` header.
```
Authorization: Bearer <valid_token>
```
3. If you are issued a `refresh_token`, [refresh](#token) the acces token when it expires


