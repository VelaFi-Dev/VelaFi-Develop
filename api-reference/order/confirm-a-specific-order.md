---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/order/confirm-a-specific-order
---

# Confirm a Specific Order

This API allows you to confirm a specific order using its order ID.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/order/confirm`
* **Authorization**: Required

**Body Parameters**

* **orderId:** (int)  The id of the order
* **orderType**: (string) The type of the order, `fiat_to_crypto crypto_to_fiat fiat_to_fiat`
* **direction:** (string)   Mark the flow direction, when the order type is fiat\_to\_fiat, this field must be filled in as `on_ramp` `off_ramp` (optional)

```json
{
    "orderId": 493829236956962817,
    "orderType": "fiat_to_fiat",
    "direction": "on_ramp"
}
```

#### Response Structure

The response will include the following fields:

* **code:** (number)  response code
* **msg**: (string) message
* data: (boolean) indicates if the confirmation was successful

```json
{
    "code": 200,        
    "msg": "SUCCESS",
    "data": true 
}
```

#### Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* Confirm that the specified `orderId` is valid and that the order is eligible for confirmation.
