# Webhooks

## Bank
```json
POST https://webhooks.test.tryflux.com/bank
[
    {
        "id": "0ba97a9c-3c27-43e3-b9cb-62a3c857a2b0",
        "userId": "4cc7c1a1-b7f2-4819-95b5-2441673539fc"
        "accountId": "da2c7d72-9b55-4238-b292-cdd033478949",
        "merchantId": "a5d43589-50c1-448f-831b-72d864c2da11 //MID",
        "merchantName": "EAT.",
        "narratives": ["EAT"]
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
]
```

Each transaction for an Flux activated user should be posted here.  The request object is an array to support multiple transactions being sent at once.  These transactions can be for multiple users or the same user.  

Max 100 transactions in a single request.  The same transaction can be posted multiple times - only the first submission will be used

Several fields are optional - it's recommended to provide as much data as possible

* `id` - The transaction ID in the banks system
* `userId` - The user ID in the banks system, in the case of a joint account this would be the user ID of the person who made the purchase
* `accountId` - The account ID for the transaction in the banks system
* `merchantId` - MID or other merchant identifier that is consistent across all stores for a single merchant
* `merchantName` - (optional - if narratives are provided) The name of the merchant
* `narratives` - (optional - if merchant name and location are provided) Can be provided instead of or in addition to merchant name and location.  The raw transaction narrative lines
* `latitude` - (optional) The latitude of the store the transaction was made at
* `longitude` - (optional) The longitude of the store the transaction was made at
* `terminalId` - (optional) The TID or terminal ID of the transaction
* `transactionDate` - The full date/time, at second resolution or better.  This must be the transaction authorization date - not the settlement date
* `amount` - The amount in minor units, ie £1.23 would be 123
* `currency` - ISO 4217 currency code
* `authCode` - (optional) The authentication code that would usually be printed on the receipt
* `card` - (optional) The card details for the transaction

## Merchant Webhook

```json
POST https://webhooks.test.tryflux.com/merchant
[
    {
        "id": "0ba97a9c-3c27-43e3-b9cb-62a3c857a2b0"
        "merchantId": "a5d43589-50c1-448f-831b-72d864c2da11 //MID",
        "terminalId": "a32df260-fd03-4429-a121-4aeeed3ee561 //TID", 
        "storeId": "43e7b609-4fb9-4825-9105-616984e02848",
        "latitude": 61.3850,
        "longitude": 152.2683,
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
]
```

Every transaction made should be posted here.  The request object is an array to support multiple transactions being sent at once.  
                                            
Max 100 transactions in a single request.  The same transaction can be posted multiple times - only the first submission will be used

* `id` - The transaction ID in the merchants system
* `merchantId` - MID or other merchant identifier that is consistent across all stores for a single merchant
* `storeId` - The store identifier in the merchants system
* `latitude` - (optional) The latitude of the store the transaction was made at
* `longitude` - (optional) The longitude of the store the transaction was made at
* `transactionDate` - The full date/time, at second resolution or better
* `amount` - The amount in minor units, ie £1.23 would be 123
* `currency` - ISO 4217 currency code
* `tax` - The tax (VAT) paid on the transaction
* `authCode` - (optional) The authentication code that would usually be printed on the receipt
* `items` - All of the items - including any special items or modifications (e.g. extra shot for a coffee)
* `card` - (optional) The card details for the transaction