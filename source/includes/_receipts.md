# Receipts

## Find by external ID
```shell
$ http https://api.test.tryflux.com/receipts/v2/external \
        external_id=0ba97a9c-3c27-43e3-b9cb-62a3c857a2b0 
```
```json
{
    "receiptIdentifier": "1234567890",
    "merchant": {
        "merchantIdentifier": "1234567890",
        "address": "123 Fake Street, London, EC2M 2AA",
        "logoUrl": "https://merchant.example.com/logo.png"
        "metadata": {
            "phone": "02072182184",
            "twitter": "#merchantsTwitter",
            "facebook": "#merchantsFacebook"
            "website": "https://merchant.example.com"
        }
    },
    "totalAmount": 974,
    "totalTax": 134,
    "taxNumber": "123 456 78901 23",
    "authCode": "123456",
    "lastFour": "1234",
    "items":[
        {
            "description": "Burger",
            "quantity": 1,
            "amount": 539,
            "tax": 77
            "modifications": [
                {
                    "description": "Extra cheese",
                    "quantity": 1,
                    "amount": 100,
                    "tax": 0
                }
            ]
        },
        {
            "description": "Fries",
            "quantity": 1,
            "amount": 139,
            "tax": 19
        },
        {
            "description": "Milkshake",
            "quantity": 2,
            "amount": 198,
            "tax": 38
        }
    ]
}
```

Retrieve a receipt by external ID.  
The `external_id` should be the `id` value that was used when posting the [webhook](#webhooks)

A 404 status indicates the no receipt was found with the given ID.  If the webhook has just been posted please try again in 10-15 seconds
<aside class="warning">
Merchant clients are not authorized to retrieve receipts
</aside>