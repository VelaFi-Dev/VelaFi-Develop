---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/basic-configuration/get-crypto-fiat-payment-methods
---

# Get Crypto/Fiat Payment Methods

This API retrieves the supported payment methods for a given cryptocurrency and fiat trading pair.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/base/sell/payments`

#### Request Parameters

The request should include the following fields:

```json
{
    "country": "Mexico",  // (string: country of the currency)
    "fiat": "USD",        // (string: name of the fiat currency)
    "crypto": "USDT"      // (string: name of the cryptocurrency)
}
```

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": { 
        "country": "Mexico",   // (string: country of the currency)
        "fiat": "USD",         // (string: name of the fiat currency)
        "crypto": "USDT",      // (string: name of the cryptocurrency)
        "paymentList": [
            { 
                "paymentId": 1,        // (string: Payment method template ID)
                "fiatFee": "2.00",     // (decimal: Fiat fee amount, unit is block)
                "paymentType": 1        // (enum: type of the payment method [0: manual, 1: automatic])
            }
        ]
    }
}
```

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "country": "Mexico",
        "fiat": "USD",
        "crypto": "USDT",
        "paymentList": [
            {
                "paymentId": 1,
                "fiatFee": "2.00",
                "paymentType": 1
            },
            {
                "paymentId": 2,
                "fiatFee": "1.50",
                "paymentType": 0
            }
            // Additional payment methods may be included
        ]
    }
}
```

#### Notes

* The `country` field specifies the country associated with the fiat currency.
* The `fiat` field provides the name of the fiat currency.
* The `crypto` field specifies the name of the cryptocurrency.
* The `paymentList` contains various payment methods supported for the specified trading pair.
* The `paymentId` is a unique identifier for each payment method.
* The `fiatFee` indicates the fee amount in fiat currency.
* The `paymentType` indicates whether the payment method is manual (0) or automatic (1).
