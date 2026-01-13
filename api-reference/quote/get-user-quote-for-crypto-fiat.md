---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/quote/get-user-quote-for-crypto-fiat
---

# Get User Quote for Crypto/Fiat

This API retrieves the current price quote for a specific cryptocurrency to fiat currency conversion. The endpoint is limited to a maximum of 60 requests per minute. If a `quoteId` is created, the `quoteId` is valid for 10 seconds.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/user/crypto-quote`
* **Authorization Required**: Yes

#### Query Parameters

* **country**: (required, string) The country for which the quote is requested.
* **from**: (required, string) The cryptocurrency token symbol (e.g., USDT).
* **to**: (required, string) The fiat currency symbol (e.g., MXN).
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
        "price": "8.9", // (string: price of the cryptocurrency in the specified fiat currency)
        "quoteId": "e46836d68a4a4a6f8f2f609352cffb2f" //(string: quote ID for this transaction, Effective time: 10 seconds)
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
* **createQuoteId**: true

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "price": "0.05",
        "quoteId": "e46836d68a4a4a6f8f2f609352cffb2f"
    }
}
```

####

#### Notes

* The `price` field represents the current conversion rate from the specified cryptocurrency to the fiat currency.
* Ensure that valid authorization tokens are included in the request headers for successful execution.
*   This `price` is for reference only and does not guarantee consistency with the order price.

    <br>
