---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/quote/get-user-quote-for-fiat-fiat
---

# Get User Quote for Fiat/Fiat

This API retrieves the current exchange rate for converting one fiat currency to another. The endpoint is limited to a maximum of 60 requests per minute. If a `quoteId` is created, the `quoteId` is valid for 10 seconds.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/user/fiat-quote`
* **Authorization Required**: Yes

#### Query Parameters

* **onRampCountry**: (required, string) Name of the country (e.g., "Mexico"))
* **onRampFiat**: (required, string) Name of the fiat currency (e.g., "MXN"))
* **offRampCountry**: (required, string) Name of the country (e.g., "Argentina"))
* **offRampFiat**: (required, string) Name of the fiat currency (e.g., "ARS"))
* **createQuoteId**: (optional, bool) Create a quote ID for this transaction. (e.g., false).

#### Authorization

This request requires authorization.

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "0.0",  // (string: price of the first fiat currency in terms of the second fiat currency)
        "quoteId": "e46836d68a4a4a6f8f2f609352cffb2f" //(string: quote ID for this transaction, Effective time: 10 seconds)
    }
}
```

#### Example Request

For example, to get the exchange rate from Mexican Pesos (MXN) to Argentine Pesos (ARS):

* **onRampCountry**: Mexico
* **onRampFiat**: MXN
* **offRampCountry**: Argentina
* **offRampFiat**: ARS

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "56.14266017"
    }
}
```

#### Example Request

For example, to get the exchange rate from Argentine Pesos (ARS) to Mexican Pesos (MXN):

* **onRampCountry**: Argentina
* **onRampFiat**: ARS
* **offRampCountry**: Mexico
* **offRampFiat**: MXN

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "0.0160686"
    }
}
```



#### Notes

* The `price` field represents the current exchange rate from the specified first fiat currency to the second fiat currency.
* Ensure that valid authorization tokens are included in the request headers for successful execution.
*   This `price` is for reference only and does not guarantee consistency with the order price.

    <br>
