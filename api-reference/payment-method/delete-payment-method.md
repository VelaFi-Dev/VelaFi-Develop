---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/payment-method/delete-payment-method
---

# Delete Payment Method

This API allows you to delete a specific payment method using its user payment ID.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `DELETE`
* **Request Path**: `/v2/payments/{userPaymentId}`
* **Authorization Required**: Yes

#### Path Parameters

* **userPaymentId**: (int) The ID of the user payment method you want to delete.

#### Authorization

This request requires authorization.

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,                        // (number: response code)
    "msg": "SUCCESS",                   // (string: message)
    "data": true                        // (boolean: indicates if the deletion was successful)
}
```

#### Example Request

To delete a payment method with `userPaymentId` of `123`:

```
DELETE /v2/payments/123
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
* Confirm that the specified `userPaymentId` exists and is eligible for deletion.
