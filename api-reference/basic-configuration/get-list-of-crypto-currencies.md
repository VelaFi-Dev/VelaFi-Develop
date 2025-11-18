---
description: Crypto
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/basic-configuration/get-list-of-crypto-currencies
---

# Get List of Crypto Currencies

This API retrieves a list of cryptocurrencies, along with their trade accuracy.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/base/cryptos`

#### Request Parameters

* **None**

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [{
        "crypto": "USDT",     // (string: name of the cryptocurrency)
        "accuracy": 6         // (number: accuracy of the trade)
    }]
}
```

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [
        {
            "crypto": "USDT",
            "accuracy": 6
        },
        {
            "crypto": "BTC",
            "accuracy": 8
        }
        // Additional cryptocurrencies may be included
    ]
}
```

#### Notes

* The `crypto` field specifies the name of the cryptocurrency.
* The `accuracy` field indicates the precision of the cryptocurrency's trade, typically representing the number of decimal places.
