---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/quote/get-user-quote-for-crypto-fiat
---

# Get User Quote for Crypto/Fiat

This API retrieves the current price quote for a specific cryptocurrency to fiat currency conversion.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/user/crypto-quote`
* **Authorization Required**: Yes

#### Query Parameters

* **country**: (string) The country for which the quote is requested.
* **from**: (string) The cryptocurrency token symbol (e.g., USDT).
* **to**: (string) The fiat currency symbol (e.g., MXN).

#### Authorization

This request requires authorization.

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "0.0"  // (string: price of the cryptocurrency in the specified fiat currency)
    }
}
```

#### Example Request

For example, to get the price of USDT in Mexican Pesos (MXN):

* **country**: Mexico
* **from**: USDT
* **to**: MXN

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "21.3707"
    }
}
```

#### Example Request

For example, to get the price of Mexican Pesos (MXN) in USDT:

* **country**: Mexico
* **from**: MXN
* **to**: USDT

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "0.05"
    }
}
```

####

#### Notes

* The `price` field represents the current conversion rate from the specified cryptocurrency to the fiat currency.
* Ensure that valid authorization tokens are included in the request headers for successful execution.
*   This `price` is for reference only and does not guarantee consistency with the order price.

    \
