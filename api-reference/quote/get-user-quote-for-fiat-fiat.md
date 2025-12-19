---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/quote/get-user-quote-for-fiat-fiat
---

# Get User Quote for Fiat/Fiat

This API retrieves the current exchange rate for converting one fiat currency to another.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/user/fiat-quote`
* **Authorization Required**: Yes

#### Query Parameters

* **onRampCountry**: (string) Name of the country (e.g., "Mexico"))
* **onRampFiat**: (string) Name of the fiat currency (e.g., "MXN"))
* **offRampCountry**: (string) Name of the country (e.g., "Argentina"))
* **offRampFiat**: (string) Name of the fiat currency (e.g., "ARS"))

#### Authorization

This request requires authorization.

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "0.0"  // (string: price of the first fiat currency in terms of the second fiat currency)
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
