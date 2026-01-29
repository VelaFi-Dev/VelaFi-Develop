# OnRamp Withdraw Message Push

This API allows you to push on-ramp to withdraw notifications to a specified webhook.

#### Endpoint Information

* **Request Method**: `POST`
* **Request Path**: (Specify the appropriate path for your webhook notifications)
* **Requesst** **Headers**: Requires signature
  * `signature` (string: To verify that a webhook request is coming from VelaFi, you can use the signature header. The value of the header is a RSA-SHA256 signature of the request body, Use hexadecimal encoding.)

#### Request Body Parameters

The request body should include the following fields:

```json
{
	"webhookId": "5a34d2887baf463ca3e1bb3648946e5d",    // (string) Unique identifier for this webhook delivery
	"eventType": "ON_RAMP_WITHDRAW_WEBHOOK",            // (string) Type of event triggered by the webhook
	"orderId": "617090742820761600",                    // (string) Platform-internal unique order identifier
	"clientId": "TEST20260128018",                      // (string) Client or merchant identifier associated with the request
	"amount": "0.73",                                   // (string) Withdrawal amount as a string to preserve precision
	"network": "POL",                                   // (string) Blockchain network code (e.g., POL for Polygon)
	"address": "0xe5fe46b5245d402cexxxxx", 							// (string) Destination on-chain address (partially masked in example)
	"txHash": "0xa7db36cb901f73a45xxxxx", 							// (string) On-chain transaction hash (partially masked in example)
	"status": "succeeded",                              // (string) Withdrawal status (possible values: succeeded, failed)
	"timestamp": "1769609100165"                        // (string) Push timestamp in milliseconds since Unix epoch
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
	"webhookId": "5a34d2887baf463ca3e1bb3648946e5d",
	"eventType": "ON_RAMP_WITHDRAW_WEBHOOK",
	"orderId": "617090742820761600",
	"clientId": "TEST20260128018",
	"amount": "0.73",               
	"network": "POL",                            
	"address": "0xe5fe46b5245d402cexxxxx",				
	"txHash": "0xa7db36cb901f73a45xxxxx",			
	"status": "succeeded",                       
	"timestamp": "1769609100165"
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
