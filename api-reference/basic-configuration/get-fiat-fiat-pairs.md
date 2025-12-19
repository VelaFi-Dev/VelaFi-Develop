---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/basic-configuration/get-fiat-fiat-pairs
---

# Get Fiat/Fiat Pairs

#### Get Fiat/Fiat Trading Pairs

This API retrieves a list of trading pairs that include fiat currencies, along with their trade accuracy.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/base/fiat/symbols`

#### Request Parameters

* **None**

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [{
        "onRampCountry": "Mexico",  // (string: Name of the country (e.g., "Mexico"))
        "onRampFiat": "MXN",        // (string: Name of the fiat currency (e.g., "MXN"))
        "offRampCountry": "HONG KONG",  // (string: Name of the country (e.g., "Mexico"))
        "offRampFiat": "USD",           // (string: Name of the fiat currency (e.g., "MXN"))
        "accuracy": 2              // (number: accuracy of the trade)
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
            "onRampCountry": "Mexico",  
            "onRampFiat": "MXN",       
            "offRampCountry": "Argentina", 
            "offRampFiat": "ARS",
            "accuracy": 2
        },
        {
            "onRampCountry": "United States",
            "onRampFiat": "USD",
            "offRampCountry": "Mexico",
            "offRampFiat": "MXN",
            "accuracy": 2
        }
        // Additional trading pairs may be included
    ]
}
```

#### Notes

* The `onRampCountry` field specifies the country associated with the originating fiat currency.
* The `onRampFiat` field provides the name of the originating fiat currency.
* The `offRampCountry` field specifies the country associated with the recipient fiat currency.
* The `offRampFiat` field provides the name of the recipient fiat currency.
* The `accuracy` field indicates the precision of the trade, typically representing the number of decimal places.
