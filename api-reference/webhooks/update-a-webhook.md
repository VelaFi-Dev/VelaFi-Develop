---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/webhooks/update-a-webhook
---

# Update a Webhook

This API allows you to update an existing webhook configuration.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `PUT`
* **Request Path**: `/v2/webhook/{webhookId}`
* **Authorization Required**: Yes

#### Request Body Parameters

The request body should include the following fields:

```json
{
    "url": "https://localhost/callback", // (string: required, callback URL)
    "status": 1                           // (number: webhook config status [10: active, 20: disabled])
}
```

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,                         // (number: response code)
    "msg": "SUCCESS",                    // (string: message)
    "data": {                            // (object: webhook data)
        "webhookId": "ebab8a9663704e7cbbebe672c7c67912", // (string: webhook ID)
        "eventType": "ORDER_WEBHOOK",    // (string: event type)
        "url": "https://localhost/callback", // (string: Merchant Transfer callback URL)
        "status": 1,                     // (number: webhook config status [10: active, 20: disabled, 30: deleted])
        "publicKey": "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAp/6GRTIrl+kQb9u27cGzXcqXbx6uA9PHQ3wGFgeBVEq0YpJxOSWpy4UmgBZ+fTOANiFyrODECWJoWIeJPOWkKR5VUseJTg57js3rgu/2Wn6Ihq1h+n6wCJEMCjK0Ia5brbQXtPcXCHK0J53hrt4YbxTzZuKUi7KIWO/Ply6xzYaTJeKzkaWlNDXF2VWBlutG+Pun3yXdWl7kTRENYA4mxXayaW0ELpnnLXF9qO01bAHPc2G8n0snqDiPMtz8Irw5MqlQ3YMjDiEDFLSb2aP9grae/o/LXZVNv0dJhV5IHgTJctDyFGz837BRiJZsBsodJK+3BTJhLsHqh6VAO8CSdQIDAQAB" // (string: optional, public key for verifying messages)
    }
}
```

#### Example Request

To update a webhook with a specific `webhookId`:

```json
{
    "url": "https://localhost/callback",
    "status": 1
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
