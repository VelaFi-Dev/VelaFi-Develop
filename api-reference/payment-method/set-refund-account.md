---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/payment-method/set-refund-account
---

# Set Refund Account

This API allows you to set a refund account for a specific payment method.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/openapi/v2/payment/refund_account`
* **Authorization Required**: Yes

#### Request Body Parameters

The request body should include the following fields:

```json
{
  "userPaymentId": 0,  (int) The ID of the user payment method.
  "merchantId": 0 (int) The ID of the merchant id.
}
```

#### Request Body Parameters

The request body should include the following fields:

```
{
  "userPaymentId": 2,         // (number: The ID of the user payment method)
  "merchantId": 6          // (number: The ID of the merchant id)  
}
```

#### Authorization

This request requires authorization.

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,                        // (number: response code)
    "msg": "SUCCESS",                   // (string: message)
    "data": true                        // (boolean: indicates if the operation was successful)
}
```

#### Example Request

To set a refund account for a payment method with `userPaymentId` of `123` and `settingsId` of `456`:

#### Example Request

```json
{
  "merchantId": 456,
  "userPaymentId": 123 
}
```

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": true
}
```

#### Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* Confirm that the specified `userPaymentId` and `settingsId` are valid and that the payment method is eligible for setting a refund account.
