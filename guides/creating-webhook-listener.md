---
icon: vector-circle
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/guides/creating-webhook-listener
---

# Creating Webhook Listener

This interface is used to create a callback URL to receive notifications for specific events. Supported event types include order events and merchant trade events.&#x20;

### Interface Information

* **Request Header**: `Content-Type: application/json`
* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `POST`
* **Request Path**: `/openapi/v2/business/webhook`
* **Authorization Required**: Yes



### Request Parameters

| Parameter Name | Type   | Required | Description                                                                                                   |
| -------------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------- |
| eventType      | string | Yes      | Event type, supported values: `ORDER_WEBHOOK` (order event), `MERCHANT_TRADE_WEBHOOK` (merchant trade event). |
| url            | string | Yes      | Callback URL for receiving event notifications.                                                               |

#### Request Example

```json
{
    "eventType": "ORDER_WEBHOOK",
    "url": "https://localhost/callback"
}
```

### Response Parameters

| Parameter Name | Type   | Description                                                                                      |
| -------------- | ------ | ------------------------------------------------------------------------------------------------ |
| code           | number | Response status code, `200` indicates success.                                                   |
| msg            | string | Response message, typically `SUCCESS`.                                                           |
| data           | object | Returned data object, containing the following fields:                                           |
| data.webhookId | string | Unique identifier for the callback URL.                                                          |
| data.eventType | string | Event type, confirming the event type specified in the request.                                  |
| data.url       | string | Merchant transfer callback URL.                                                                  |
| data.status    | number | Callback configuration status, supported values: `10` (active), `20` (disabled), `30` (deleted). |
| data.publicKey | string | (Optional) Public key of RSA-SHA256, used to verify push messages.                               |

#### Response Example

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "webhookId": "ebab8a9663704e7cbbebe672c7c67912",
        "eventType": "ORDER_WEBHOOK",
        "url": "https://localhost/callback",
        "status": 1,
        "publicKey": "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAp/6GRTIrl+kQb9u27cGzXcqXbx6uA9PHQ3wGFgeBVEq0YpJxOSWpy4UmgBZ+fTOANiFyrODECWJoWIeJPOWkKR5VUseJTg57js3rgu/2Wn6Ihq1h+n6wCJEMCjK0Ia5brbQXtPcXCHK0J53hrt4YbxTzZuKUi7KIWO/Ply6xzYaTJeKzkaWlNDXF2VWBlutG+Pun3yXdWl7kTRENYA4mxXayaW0ELpnnLXF9qO01bAHPc2G8n0snqDiPMtz8Irw5MqlQ3YMjDiEDFLSb2aP9grae/o/LXZVNv0dJhV5IHgTJctDyFGz837BRiJZsBsodJK+3BTJhLsHqh6VAO8CSdQIDAQAB"
    }
}
```

### Notes

* Ensure that the provided callback URL is valid and capable of handling POST requests.
* The event type must be one of the supported types.
* The public key is an optional field, used only when verification of push messages is required.
