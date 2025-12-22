---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/basic-configuration/get-list-of-fiat-currencies
---

# Get List of Fiat Currencies

This API retrieves a list of fiat currencies, along with their associated countries and trade accuracy.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/base/fiats`

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
        "fiat": "USD",        // (string: name of the currency)
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
            "country": "Mexico",
            "fiat": "MXN",
            "accuracy": 2
        },
        {
            "country": "United States",
            "fiat": "USD",
            "accuracy": 2
        }
        // Additional fiat currencies may be included
    ]
}
```

#### Notes

* The `country` field specifies the country associated with the fiat currency.
* The `fiat` field provides the name of the currency.
* The `accuracy` field indicates the precision of the currency's trade, typically representing the number of decimal places.
