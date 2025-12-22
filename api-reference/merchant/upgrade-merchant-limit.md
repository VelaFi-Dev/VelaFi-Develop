# Upgrade Merchant Limit

This API allows merchants to initiate a **merchant limit upgrade verification** process when requesting higher transaction or balance limits.

If your business or operational needs exceed the default limits, you may apply for an increased limit by submitting additional compliance documents — such as proof of source of funds, business licenses, or audited financial statements.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/upgrade/limits`
* **Authorization Required**: Yes



**Request Parameters**The request body should include the following fields:

```json
{     
    "merchantId": 151209, //(required, string: Merchant id)  
    "callbackUrl": "https://localhost" //(required, string: URL for KYC/KYB completion callback) 
}
```

**Response Structure**The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {     
        "link": "https://www.velafi.com/verify?velafi_token=abc123" //(string: Link for conducting upgrade merchant limit)
    }
}
```

