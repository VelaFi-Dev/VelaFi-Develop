---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/webhooks/delete-a-webhook
---

# Delete a Webhook

This API allows you to delete an existing webhook configuration.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `DELETE`
* **Request Path**: `/v2/webhook/{webhookId}`
* **Authorization Required**: Yes

#### Path Parameter

* **webhookId**: (string) The ID of the webhook you want to delete.

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,                        // (number: response code)
    "msg": "SUCCESS",                   // (string: message)
    "data": {                           // (object: deletion result)
        "result": true                  // (boolean: indicates if the deletion was successful)
    }
}
```

#### Example Request

To delete a webhook with a specific `webhookId`:

```
DELETE /v2/webhook/ebab8a9663704e7cbbebe672c7c67912
```

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "result": true
    }
}
```

#### Notes

* Ensure that valid authorization tokens are included in the request headers for successful execution.
* Once deleted, the webhook configuration cannot be recovered.
