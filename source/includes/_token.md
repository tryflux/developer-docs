# Token

## Create a new token
```shell
$ http --form POST https://api.test.tryflux.com/auth/oauth/token \
    client_id='<your_client_id>' \
    client_secret='<your_client_secret' \
    grant_type='client_credentials'
    scope='<your_user_id>(optional)'
```
```json
{
    "access_token": "eyJhbGciOiJSUzI1NiIsInppcCI6IkdaSVAifQ.H4sIAAAAAAAAAG2QXU_CMBSG_4o5l2aFMvfVJV4wNUIQRnQYxHrRbh1U2UfWoiyE_25nDEbjzXtynvPkvTgHeNUSQuCYsNS_4MjBJDPhc8SxS1BAiO0ybLOUDcACqZSRddPm292-l1aFYWyXGeZhW_AgZ4h7wkOOkwWIeDlHeeAGjm3S5b6Rxb6GcOAOsEOw7dsWlDz_BoHndaAQmmVMM9N5oJBupSh10taCQkiBUgrRcDbpJgWLgpLrUpbraZX9CPE8Gcez4d1faSLak6OGbPWu9OZx_aYTlo756GkZTe-3H6yqltFVUcSrRT26xnlfXZ56atEU5gOyKtVX0XN3mS-Ssz7b6U2_d97tVhe3N__Aefzwm75QOJqfNELpRqZaZEkF4eF4_ASh9oBSlQEAAA.lhFAvvhm52GcKw-n89T-eUTgVjM5ygsLnwxz_gazXQePpoRD9dAULE2aDhNF5FUl5c2Ix9d36xR0rajoNJ_GmQ",
    "refresh_token": "JT911IQ03V+Gs81Jcut8smRDvU+ssGCl6HPfbHa+2YDbPGITkuVX1naHDKQOXCJqyKphhIJRyXX1OGEbY/ARyg==",
    "token_type": "bearer",
    "expires_in": 3600
}
```
Issue a new token using your `client_id` and `client_secret`

* `scope` - (optional) The user id that this token should be restricted to.  If excluded the token will be valid for all users that are authorized for the client id 

## Refresh a token
```shell
$ http --form POST https://api.test.tryflux.com/auth/oauth/token \
        refresh_token='<the_refresh_token' \ 
        grant_type='refresh_token'
```
```json
{
    "access_token": "eyJhbGciOiJSUzI1NiIsInppcCI6IkdaSVAifQ.H4sIAAAAAAAAAG2QXU_CMBSG_4o5l2aFMvfVJV4wNUIQRnQYxHrRbh1U2UfWoiyE_25nDEbjzXtynvPkvTgHeNUSQuCYsNS_4MjBJDPhc8SxS1BAiO0ybLOUDcACqZSRddPm292-l1aFYWyXGeZhW_AgZ4h7wkOOkwWIeDlHeeAGjm3S5b6Rxb6GcOAOsEOw7dsWlDz_BoHndaAQmmVMM9N5oJBupSh10taCQkiBUgrRcDbpJgWLgpLrUpbraZX9CPE8Gcez4d1faSLak6OGbPWu9OZx_aYTlo756GkZTe-3H6yqltFVUcSrRT26xnlfXZ56atEU5gOyKtVX0XN3mS-Ssz7b6U2_d97tVhe3N__Aefzwm75QOJqfNELpRqZaZEkF4eF4_ASh9oBSlQEAAA.lhFAvvhm52GcKw-n89T-eUTgVjM5ygsLnwxz_gazXQePpoRD9dAULE2aDhNF5FUl5c2Ix9d36xR0rajoNJ_GmQ",
    "refresh_token": "JT911IQ03V+Gs81Jcut8smRDvU+ssGCl6HPfbHa+2YDbPGITkuVX1naHDKQOXCJqyKphhIJRyXX1OGEbY/ARyg==",
    "token_type": "bearer",
    "expires_in": 3600
}
```

Generate a new access token using the `refresh_token` field returned from when the original access token was issued
