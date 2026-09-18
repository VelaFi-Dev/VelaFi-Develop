# Get Woovi liveness URL

This endpoint is the URL for obtaining the Woovi live verification.



**Endpoint Information**

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Header:** `Content-Type: application/json`
* **Request Method:** POST
* **Request Path:** `/v2/merchant/woovi/liveness`
* **Authorization Required:** Yes

**Request Parameters**

The request body should include the following fields:

```json
{         
    "merchantId": 151209, //(required, string: Merchant id) 
    "generateNewLiveness":false // (optional, boolean: true/false,Regenerate liveness) 
}
```

**Response Structure**

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "livenessId": "035236af-c51e-4b12-af1a-7cbd26e59c0b", // (string: ID of the liveness) 
        "livenessUrl": "https://app.sandbox.io/liveness/3744e440-2880-468?jwt=eyJhbGciOiJIUzI...", // (string: url of the liveness) 
        "expiresAt": "1788244424", // (number: timestamp of the expiration time in seconds) 
        "status": "PENDING", // (string: status [PENDING: Pending liveness, COMPLETED: Liveness check completed, KYC_APPROVED: KYC review completed])
        "failReason": "" //(string: fail reason of the liveness) 
    }
}
```

**Example Request**

```json
{         
    "merchantId": 151209,
    "generateNewLiveness":false 
}
```

**Example Response**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "livenessId": "035236af-c51e-4b12-af1a-7cbd26e59c0b",
        "livenessUrl": "https://app.sandbox.avenia.io/liveness/3744e440-2880-468c-8204-b992e4213e90?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3ODgyNDQ0MjQsImlhdCI6MTc4ODI0NDEyNCwic2Vzc2lvbklkIjoiMzc0NGU0NDAtMjg4MC00NjhjLTgyMDQtYjk5MmU0MjEzZTkwIiwic3ViIjoiMDM1MjM2YWYtYzUxZS00YjEyLWFmMWEtN2NiZDI2ZTU5YzBiIn0.LiD-iQ8dAsv2Mei3GOwltBgp76Tuv73Bn50t6m7PFgE",
        "expiresAt": "1788244424",
        "status": "PENDING",
        "failReason": ""
    }
}
```

#### Notes

* Ensure to provide valid parameters for successful order creation.
* The response will confirm the successful creation of the order along with the `txId` for tracking.
