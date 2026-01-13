---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/webhooks/fiat-crypto-order-message-push
---

# Fiat/Crypto Order Message Push

This API allows you to push order notifications to a specified webhook.

#### Endpoint Information

* **Request Method**: `POST`
* **Request Path**: (Specify the appropriate path for your webhook notifications)
* **Requesst** **Headers**: Requires signature
  * `signature` (string: To verify that a webhook request is coming from VelaFi, you can use the signature header. The value of the header is a RSA-SHA256 signature of the request body, Use hexadecimal encoding.)

#### Request Body Parameters

The request body should include the following fields:

```json
{
    "webhookId": "ebab8a9663704e7cbbebe672c7c67912",  // (string: ID of the webhook)
    "eventType": "ORDER_WEBHOOK",                    // (string: event type [ORDER_WEBHOOK])
    "orderId": "473130522693193728",                 // (string: ID of the order)
    "clientId": "W658784738723",                     // (string: ID of the client)
    "userId": "455472",                              // (string: ID of the user)
    "merchantId": 4,                                 // (number: ID of the merchant)   
    "orderType": "SELL",                             // (string: order type [BUY or SELL])
    "fiat": "MXN",                                   // (string: name of the fiat currency)
    "fiatAmount": "99",                             // (decimal: amount of fiat currency)
    "fiatFee": "0",                                  // (decimal: fiat fee)
    "crypto": "USDT",                                // (string: name of the crypto currency)
    "cryptoAmount": "5.00",                          // (decimal: amount of crypto currency)
    "orderPrice": "19.8158",                         // (decimal: order price)
    "orderStatus": "60",                             // (string: order status [10, 30, 40, 50, 60, 70])
    "failCode": "",                                  // (string: order failed code)
    "failReason": "",                                // (string: order failure description)
    "createTime": "1735279907000",                  // (string: timestamp of the create time in milliseconds)
    "updateTime": "1735280582000"                   // (string: timestamp of the update time in milliseconds)
}
```

#### Response Structure

The response will include the following fields:

```json
{
    "callbackStatus": "SUCCESS"                      // (string: callback status, indicates if the message was successfully notified)
}
```

#### Example Request

```json
{
    "webhookId": "ebab8a9663704e7cbbebe672c7c67912",
    "eventType": "ORDER_WEBHOOK",
    "orderId": "473130522693193728",
    "clientId": "W658784738723",
    "userId": "455472",
    "merchantId": 4,    
    "orderType": "SELL",
    "fiat": "MXN",
    "orderAmount": "99",
    "fiatFee": "0",
    "crypto": "USDT",
    "quantity": "5",
    "orderPrice": "19.8158",
    "orderStatus": "60",
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
