---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/basic-configuration/get-fiat-fiat-payment-methods
---

# Get Fiat/Fiat Payment Methods

This API retrieves the supported payment methods for converting one fiat currency to another, including the details for both the originating and recipient currencies.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/base/fiat/payments`

#### Request Parameters

The request should include the following fields:

```json
{
    "onRampCountry": "Mexico",  // (string: Name of the country (e.g., "Mexico"))
    "onRampFiat": "MXN",        // (string: Name of the fiat currency (e.g., "MXN"))
    "offRampCountry": "Argentina",  // (string: Name of the country (e.g., "Argentina"))
    "offRampFiat": "ARS"           // (string: Name of the fiat currency (e.g., "ARS"))
}
```

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": { 
        "onRampCountry": "Mexico",  // (string: Name of the country (e.g., "Mexico"))
        "onRampFiat": "MXN",        // (string: Name of the fiat currency (e.g., "MXN"))
        "offRampCountry": "Argentina",  // (string: Name of the country (e.g., "Argentina"))
        "offRampFiat": "ARS",           // (string: Name of the fiat currency (e.g., "ARS"))
        "paymentListFrom": [        // (array: list of supported payment methods for the originating currency)
            { 
                "paymentId": 1,        // (string: Payment method template ID)
                "fiatFee": "2",         // (decimal: Fiat fee amount, unit is block)
                "paymentType": 1        // (enum: type of the payment method [0: manual, 1: automatic])
            }
        ],
        "paymentListTo": [          // (array: list of supported payment methods for the recipient currency)
            { 
                "paymentId": 1,        // (string: Payment method template ID)
                "fiatFee": "2",         // (decimal: Fiat fee amount, unit is block)
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
        "onRampCountry": "Mexico",
        "onRampFiat": "MXN",
        "offRampCountry": "Argentina",
        "offRampFiat": "ARS",
        "paymentListFrom": [
            {
                "paymentId": 1,
                "fiatFee": "2",
                "paymentType": 1
            },
            {
                "paymentId": 2,
                "fiatFee": "1.50",
                "paymentType": 0
            }
        ],
        "paymentListTo": [
            {
                "paymentId": 1,
                "fiatFee": "2",
                "paymentType": 1
            },
            {
                "paymentId": 3,
                "fiatFee": "1.75",
                "paymentType": 0
            }
        ]
    }
}
```

#### Notes

* The `countryFrom` field specifies the country associated with the originating fiat currency.
* The `fiatFrom` field provides the name of the originating fiat currency.
* The `countryTo` field specifies the country associated with the recipient fiat currency.
* The `fiatTo` field provides the name of the recipient fiat currency.
* The `paymentListFrom` contains various payment methods supported for the originating fiat currency.
* The `paymentListTo` contains various payment methods supported for the recipient fiat currency.
* The `paymentId` is a unique identifier for each payment method.
* The `fiatFee` indicates the fee amount in fiat currency.
* The `paymentType` indicates whether the payment method is manual (0) or automatic (1).
