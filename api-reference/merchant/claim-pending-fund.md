---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/merchant/claim-pending-fund
---

# Claim Pending Fund

This endpoint enables you to withdraw the available balance from your VelaFi Fund account to your specified payment method. Withdrawals can be initiated at any time, allowing for flexible and timely fund management.



**Endpoint Information**

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Header:** `Content-Type: application/json`
* **Request Method:** POST
* **Request Path:** `/v2/merchant/claimfunds`
* **Authorization Required:** Yes

**Request Parameters**

The request body should include the following fields:

```json
{         
    "merchantId": 3,           // (number: ID of the merchant) required 
    "clientId": "1748536001",  // (string: An order ID that you may define and it is the only one) optional
    "fiat": "MXN",             // (string: name of the fiat currency; MXN and ARS are currently supported) required 
    "amount": 20.00,           // (decimal: fiat amount) required 
    "userPaymentId": 91        // (number: ID of the user payment method; obtainable via GET /v2/payments) required    
} 
```

**Response Structure**

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "txId": 1123123123,       // (number: ID of the fiat withdraw)        
        "merchantId": 3,          // (number: ID of the merchant)
        "clientId": "1748536001", // (string: ID of the client)
        "fiat": "MXN",            // (string: name of the fiat currency) 
        "totalAmount": 22.00,     // (decimal: total fiat amount)
        "amount": 20.00,          // (decimal: actual fiat amount)
        "fee": 2.00,              // (decimal: amount of the fee)
        "userPaymentId": 91,      // (number: ID of the user payment method) 
        "status": 1,              // (enum: status [1: pending, 2: completed, 3: canceled])       
        "createTime": "1737452292000" // (string: timestamp of the create time in milliseconds) 
    }
}
```

**Example Request**

```json
{         
    "merchantId": 3,
    "clientId": "1748536001",
    "fiat": "MXN", 
    "amount": 20.00, 
    "userPaymentId": 91
} 
```

**Example Response**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "txId": 1123123123,      
        "merchantId": 3,
        "clientId": "1748536001",
        "fiat": "MXN",
        "totalAmount": 22.00, 
        "amount": 20.00, 
        "fee": 2.00, 
        "userPaymentId": 91,
        "status": 1,    
        "createTime": "1737452292000"
    }
}
```

#### Notes

* Ensure to provide valid parameters for successful order creation.
* The response will confirm the successful creation of the order along with the `txId` for tracking.
