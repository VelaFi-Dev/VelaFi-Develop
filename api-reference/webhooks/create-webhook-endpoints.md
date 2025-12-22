---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/webhooks/create-webhook-endpoints
---

# Create Webhook Endpoints

This API allows you to create a callback URL for receiving event notifications.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/webhook`
* **Authorization Required**: Yes

#### Request Body Parameters

The request body should include the following fields:

```json
{
    "eventType": "ORDER_WEBHOOK",     // (string: required, event type [ORDER_WEBHOOK, GLOBAL_PAYMENT_WEBHOOK, FUNDING_WEBHOOK])
    "url": "https://localhost/callback"        // (string: required, callback URL)
}
```

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,                        // (number: response code)
    "msg": "SUCCESS",                   // (string: message)
    "data": {                           // (object: webhook data)
        "webhookId": "ebab8a9663704e7cbbebe672c7c67912", // (string: webhook ID)
        "eventType": "ORDER_WEBHOOK",  // (string: event type)
        "url": "https://localhost/callback", // (string: Merchant Transfer callback URL)
        "status": 1,                    // (number: webhook config status [10: active, 20: disabled, 30: deleted])
        "publicKey": "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAp/6GRTIrl+kQb9u27cGzXcqXbx6uA9PHQ3wGFgeBVEq0YpJxOSWpy4UmgBZ+fTOANiFyrODECWJoWIeJPOWkKR5VUseJTg57js3rgu/2Wn6Ihq1h+n6wCJEMCjK0Ia5brbQXtPcXCHK0J53hrt4YbxTzZuKUi7KIWO/Ply6xzYaTJeKzkaWlNDXF2VWBlutG+Pun3yXdWl7kTRENYA4mxXayaW0ELpnnLXF9qO01bAHPc2G8n0snqDiPMtz8Irw5MqlQ3YMjDiEDFLSb2aP9grae/o/LXZVNv0dJhV5IHgTJctDyFGz837BRiJZsBsodJK+3BTJhLsHqh6VAO8CSdQIDAQAB" // (string: optional, public key for verifying messages)
    }
}
```

#### Example Request

To create a webhook for order events:

```json
{
    "eventType": "ORDER_WEBHOOK",
    "url": "https://localhost/callback"
}
```

#### Example Response

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

#### Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* The `publicKey` can be used to verify the integrity of the messages received at the callback URL.
