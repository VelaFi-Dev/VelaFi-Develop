---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/webhooks/get-webhook-endpoints
---

# Get Webhook Endpoints

This API allows you to retrieve a list of webhook configurations based on their status.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/webhooks`
* **Authorization Required**: Yes

#### Query Parameter

* **status**: (int) The status of the webhooks to filter by:
  * `10`: active
  * `20`: disabled
  * `30`: deleted

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,                        // (number: response code)
    "msg": "SUCCESS",                   // (string: message)
    "data": [                           // (array: list of webhooks)
        {  
            "webhookId": "ebab8a9663704e7cbbebe672c7c67912", // (string: webhook ID)
            "eventType": "ORDER_WEBHOOK", // (string: event type)
            "url": "https://localhost/callback", // (string: Merchant Transfer callback URL)
            "status": 1,                // (number: webhook config status)
            "publicKey": "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAp/6GRTIrl+kQb9u27cGzXcqXbx6uA9PHQ3wGFgeBVEq0YpJxOSWpy4UmgBZ+fTOANiFyrODECWJoWIeJPOWkKR5VUseJTg57js3rgu/2Wn6Ihq1h+n6wCJEMCjK0Ia5brbQXtPcXCHK0J53hrt4YbxTzZuKUi7KIWO/Ply6xzYaTJeKzkaWlNDXF2VWBlutG+Pun3yXdWl7kTRENYA4mxXayaW0ELpnnLXF9qO01bAHPc2G8n0snqDiPMtz8Irw5MqlQ3YMjDiEDFLSb2aP9grae/o/LXZVNv0dJhV5IHgTJctDyFGz837BRiJZsBsodJK+3BTJhLsHqh6VAO8CSdQIDAQAB" // (string: optional, public key for verifying messages)
        }
    ]
}
```

#### Example Request

To query active webhooks:

```
GET /v2/webhooks?status=10
```

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [
        {  
            "webhookId": "ebab8a9663704e7cbbebe672c7c67912",
            "eventType": "ORDER_WEBHOOK",
            "url": "https://localhost/callback",
            "status": 1,
            "publicKey": "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAp/6GRTIrl+kQb9u27cGzXcqXbx6uA9PHQ3wGFgeBVEq0YpJxOSWpy4UmgBZ+fTOANiFyrODECWJoWIeJPOWkKR5VUseJTg57js3rgu/2Wn6Ihq1h+n6wCJEMCjK0Ia5brbQXtPcXCHK0J53hrt4YbxTzZuKUi7KIWO/Ply6xzYaTJeKzkaWlNDXF2VWBlutG+Pun3yXdWl7kTRENYA4mxXayaW0ELpnnLXF9qO01bAHPc2G8n0snqDiPMtz8Irw5MqlQ3YMjDiEDFLSb2aP9grae/o/LXZVNv0dJhV5IHgTJctDyFGz837BRiJZsBsodJK+3BTJhLsHqh6VAO8CSdQIDAQAB"
        }
    ]
}
```

#### Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* The `publicKey` can be used to verify the integrity of the messages received at the webhook URL.
