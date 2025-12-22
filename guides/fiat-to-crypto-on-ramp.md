---
icon: bitcoin-sign
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/guides/fiat-to-crypto-on-ramp
---

# Fiat to Crypto (On-Ramp)

This section provides information about the fiat to crypto on-ramp process, allowing users to convert fiat currency into cryptocurrency through the API.

## **Create Order**

* **Request Header**: `Content-Type: application/json`
* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `POST`
* **Request Path:** `/v2/order/fiat_to_crypto`
* **Authorization Required**: Yes



**Request Parameters**

The request body should include the following parameters:

| Parameter                         | Type    | Required | Description                                                                      |
| --------------------------------- | ------- | -------- | -------------------------------------------------------------------------------- |
| country                           | string  | Yes      | Name of the country (e.g., "Mexico")                                             |
| clientId                          | string  | No       | An order ID that you may define and will be returned to you in a Get Order call. |
| merchantId                        | number  | No       | ID of the merchant                                                               |
| crypto                            | string  | Yes      | Name of the cryptocurrency (e.g., "USDT")                                        |
| fiat                              | string  | Yes      | Name of the fiat currency (e.g., "MXN")                                          |
| fiatAmount                        | decimal | Yes      | Amount of fiat currency to convert (e.g., 1000.00)                               |
| [paymentId](payment-method-id.md) | number  | Yes      | ID of the payment method                                                         |
| remark                            | string  | No       | Additional remarks for the order                                                 |

**Request Example**

```json
{
    "country": "Mexico",
    "clientId": "xxxx",
    "merchantId": 3,
    "crypto": "USDT",
    "fiat": "MXN",
    "fiatAmount": 1000.00,
    "paymentId": 91,
    "remark": ""
}
```

**Response Parameters**

The response will contain the following parameters:

| Parameter    | Type   | Description                        |
| ------------ | ------ | ---------------------------------- |
| code         | number | Response status code (e.g., 200)   |
| msg          | string | Response message (e.g., "SUCCESS") |
| data         | object | Contains order details             |
| data.orderId | number | ID of the created order            |

**Response Example**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "orderId": 1123123123
    }
}
```

### Notes

* Ensure that valid parameters are provided for successful order creation.
* The `merchantId` and `paymentId` must correspond to existing merchant and payment method configurations.
* The response will confirm the successful creation of the order, along with the order ID for tracking.
