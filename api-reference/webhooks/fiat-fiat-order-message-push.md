---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/webhooks/fiat-fiat-order-message-push
---

# Fiat/Fiat Order Message Push

This API allows you to push global payment order notifications to a specified webhook.

#### Endpoint Information

* **Request Method**: `POST`
* **Request Path**: (Specify the appropriate path for your webhook notifications)
* **Requesst** **Headers**: Requires signature
  * `signature` (string: To verify that a webhook request is coming from trubit, you can use the signature header. The value of the header is a RSA-SHA256 signature of the request body, Use hexadecimal encoding.)

#### Request Body Parameters

The request body should include the following fields:

```json
{
    "webhookId": "ebab8a9663704e7cbbebe672c7c67912",  // (string: ID of the webhook)
    "eventType": "GLOBAL_PAYMENT_WEBHOOK",            // (string: event type [GLOBAL_PAYMENT_WEBHOOK])
    "orderId": "473130522693193728",                  // (string: ID of the order)
    "clientId": "W658784738723",                      // (string: ID of the client)
    "userId": "455472",                               // (string: ID of the user)        
    "onRampCountry": "Mexico",                        // (string: name of the on-ramp country)
    "onRampMerchantId": 3,                            // (number: ID of the on-ramp merchant id)
    "onRampFiat": "MXN",                              // (string: name of the on-ramp fiat currency)
    "onRampFiatAmount": "100.00",                     // (decimal: amount of on-ramp fiat currency)
    "onRampFiatFee": "0",                             // (decimal: amount of on-ramp fiat fee)    
    "offRampCountry": "Hong Kong",                    // (string: name of the off-ramp country)
    "offRampMerchantId": 4,                           // (number: ID of the off-ramp merchant id)
    "offRampFiat": "USD",                             // (string: name of the off-ramp fiat currency)
    "offRampFiatAmount": "18.00",                     // (decimal: amount of off-ramp fiat currency)
    "offRampFiatFee": "2.00",                         // (decimal: amount of off-ramp fiat fee)    
    "orderPrice": "20.00",                            // (decimal: price of the order)
    "orderStatus": "41",                              // (string: order status [10, 30, 31, 41, 51, 60, 71, 72])
    "createTime": "1735279907000",                    // (string: timestamp of the create time in milliseconds)
    "updateTime": "1735280582000"                     // (string: timestamp of the update time in milliseconds)
}
```

#### Response Structure

The response will include the following fields:

```json
{
    "callbackStatus": "SUCCESS"                       // (string: callback status, indicates if the message was successfully notified)
}
```

#### Example Request

```json
{
    "webhookId": "ebab8a9663704e7cbbebe672c7c67912",
    "eventType": "GLOBAL_PAYMENT_WEBHOOK",
    "orderId": "473130522693193728",
    "clientId": "W658784738723",
    "userId": "455472",
    "onRampCountry": "Mexico",
    "onRampMerchantId": 3,
    "onRampFiat": "MXN",
    "onRampFiatAmount": "100.00",
    "onRampFiatFee": "0",
    "offRampCountry": "Hong Kong",
    "offRampMerchantId": 4,
    "offRampFiat": "USD",
    "offRampFiatAmount": "18.00",
    "offRampFiatFee": "2.00",
    "orderPrice": "20.00",
    "orderStatus": "41",
    "createTime": "1735279907000",
    "updateTime": "1735280582000"
}
```

#### Example Response

```json
{
    "callbackStatus": "SUCCESS"
}
```

#### Notes

* Ensure that the webhook URL is properly configured to receive and process the notification.
* The `callbackStatus` indicates whether the message was successfully sent to the webhook. If it shows `SUCCESS`, the notification was sent without issues.
