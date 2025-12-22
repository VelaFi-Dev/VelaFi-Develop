---
description: >-
  This section provides information about the fiat to fiat process, allowing
  users to convert fiat currency into cryptocurrency through the API.
icon: earth-americas
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/guides/fiat-to-fiat-global-payment
---

# Fiat to Fiat (Global Payment)

## **Create Order**

* **Request Header**: `Content-Type: application/json`
* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `POST`
* **Request Path:** `/v2/order/fiat_to_fiat`
* **Authorization Required**: Yes

**Request Parameters**

The request body should include the following parameters:

<table><thead><tr><th width="266">Parameter</th><th width="96">Type</th><th>Required</th><th>Description</th></tr></thead><tbody><tr><td>clientId</td><td>string</td><td>No</td><td>Unique identifier for the client</td></tr><tr><td>onRampCountry</td><td>string</td><td>Yes</td><td>Name of the country (e.g., "Mexico")</td></tr><tr><td>onRampMerchantId</td><td>number</td><td>No</td><td>ID of the merchant</td></tr><tr><td>onRampFiat</td><td>string</td><td>Yes</td><td>Name of the fiat currency (e.g., "MXN")</td></tr><tr><td>onRampFiatAmount</td><td>decimal</td><td>Yes</td><td>Amount of fiat currency to convert (e.g., 1000.00)</td></tr><tr><td><a href="payment-method-id.md">onRampPaymentId</a></td><td>number</td><td>Yes</td><td>ID of the payment method</td></tr><tr><td>offRampCountry</td><td>string</td><td>Yes</td><td>Name of the country (e.g., "Mexico")</td></tr><tr><td>offRampMerchantId</td><td>number</td><td>No</td><td>ID of the merchant</td></tr><tr><td>offRampFiat</td><td>decimal</td><td>Yes</td><td>Name of the fiat currency (e.g., "MXN")</td></tr><tr><td><a href="../api-reference/payment-method/get-payment-method.md">offRampPaymentId</a></td><td>number</td><td>Yes</td><td>ID of the payment method</td></tr><tr><td>remark</td><td>string</td><td>No</td><td>Additional remarks for the order</td></tr></tbody></table>

**Request Example**

```json

{
    "clientId": "xxxx",
    "onRampCountry": "Mexico",
    "onRampMerchantId": 12345,
    "onRampFiat": "MXN",
    "onRampFiatAmount": 1000.00,
    "onRampPaymentId": 91,
    "offRampCountry": "HONGKONG",
    "offRampMerchantId": 54321,
    "offRampFiat": "USD",
    "offRampPaymentId": 77,
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

* Ensure to provide valid parameters for successful order creation.
* The `merchantId`  and `paymentId` must correspond to existing merchant and payment method configurations.
* The response will confirm the successful creation of the order along with the order ID for tracking.



