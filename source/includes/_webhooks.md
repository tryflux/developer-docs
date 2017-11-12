# Webhooks

## Bank
```json
POST https://webhooks.test.tryflux.com/bank

    {
        "id": "0ba97a9c-3c27-43e3-b9cb-62a3c857a2b0",
        "accountId": "da2c7d72-9b55-4238-b292-cdd033478949",
        "merchantId": "a5d43589-50c1-448f-831b-72d864c2da11 //MID",
        "merchantName": "EAT.",
        "merchantAddress": "95 City Road",
        "latitude": 61.3850,
        "longitude": 152.2683,
        "terminalId": "a32df260-fd03-4429-a121-4aeeed3ee561 //TID", 
        "transactionDate": "2017-06-05T09:56:01Z",
        "amount": 235,
        "currency": "GBP",
        "authCode": "123456",
        "card": {
            "scheme": "MASTERCARD",
            "lastFour": "1234"
            "bin": "456789",
        }
    }
```

Each transaction for an Flux activated user should be posted here

## Merchant Webhook

```json
POST https://webhooks.test.tryflux.com/merchant

    {
        "id": "0ba97a9c-3c27-43e3-b9cb-62a3c857a2b0"
        "merchantId": "a5d43589-50c1-448f-831b-72d864c2da11 //MID",
        "terminalId": "a32df260-fd03-4429-a121-4aeeed3ee561 //TID", 
        "storeId": "43e7b609-4fb9-4825-9105-616984e02848",
        "transactionDate": "2017-06-05T09:56:01Z",
        "amount": 235,
        "currency": "GBP",
        "tax": 39,
        "authCode": "123456",
        "items": [
            {
                "sku": "21412",
                "description": "Cappuccino",
                "category": "Hot drinks",
                "quantity": 1,
                "price": 235,
                "tax": 39,
            }
        ],
        "card": {
            "scheme": "MASTERCARD",
            "lastFour": "1234"
            "bin": "456789",
        }
    }
```

Every transaction made should be posted here