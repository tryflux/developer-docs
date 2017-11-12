# Request Signing

```
# String to Sign: 
1509731334
EJbYLPSvMD7rsu7i4hJeyjTrhLbK
api.test.tryflux.com
/receipts/v2/external
externalId=0d5e0f95-d3e0-47ba-aa89-7306dc76f229

# Using example key
sAaZvsthVgktTacIbHYXBMRlwaooXBCmmOZUpHD0f/s=

# Resulting hash
tdblOhhGXNPVIv5SNiwsk+NsySubqUocdjCEe4DmUBg=

# Resulting header
X-Request-Signature: HMacSHA256:1509731334:EJbYLPSvMD7rsu7i4hJeyjTrhLbK:tdblOhhGXNPVIv5SNiwsk+NsySubqUocdjCEe4DmUBg=
```

Optionally, request signing can be enabled to provide an extra layer of security.  If request signing is enabled a `signing_key` will be returned when an access token is create via the [token](#token) resource
To sign a request:
  
1. Construct the string to be signed by concatenating the current epoch second, a random nonce, the request method, request host, request url and request body (if present).  Separating each element with a new line

2. Hash this string using the `signing_key` and `signing_algorithm` indicated in the [token](token) response

3. Base64 encode the hashed value

4. Include the following header with the request `X-Request-Signature: HmacSHA256:epoch_second:nonce:signature`

