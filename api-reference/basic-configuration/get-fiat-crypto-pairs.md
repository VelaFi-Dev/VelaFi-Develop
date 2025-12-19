---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/basic-configuration/get-fiat-crypto-pairs
---

# Get Fiat/Crypto Pairs

This API retrieves a list of trading pairs that include both fiat currencies and cryptocurrencies, along with their trade accuracy.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/base/buy/symbols`

#### Request Parameters

* **None**

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [{
        "country": "Mexico",  // (string: country of the currency)
        "fiat": "USD",        // (string: name of the fiat currency)
        "crypto": "USDT",     // (string: name of the cryptocurrency)
        "accuracy": 2         // (number: accuracy of the trade)
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
            "country": "Mexico",
            "fiat": "MXN",
            "crypto": "BTC",
            "accuracy": 2
        },
        {
            "country": "United States",
            "fiat": "USD",
            "crypto": "ETH",
            "accuracy": 2
        }
        // Additional trading pairs may be included
    ]
}
```

#### Notes

* The `country` field specifies the country associated with the fiat currency.
* The `fiat` field provides the name of the fiat currency.
* The `crypto` field specifies the name of the cryptocurrency.
* The `accuracy` field indicates the precision of the trade, typically representing the number of decimal places.
