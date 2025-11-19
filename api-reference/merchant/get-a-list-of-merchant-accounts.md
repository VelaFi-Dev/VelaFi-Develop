---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/get-a-list-of-merchant-accounts
---

# Get a List of Merchant Accounts

This API retrieves a list of accounts associated with merchants based on optional query parameters.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/merchant/accounts`
* **Authorization Required**: Yes

#### Query Parameters

* **merchantId**: (int) The ID (MID) associated with the Merchant (optional).
* **merchantName**: (string) The name of the merchant (optional).
* **email**: (string) The email of the merchant (optional).
* **fiat**: (string) The fiat currency (optional).
* **status**: (int) The status of the merchant \[1: authenticating, 2: normal, 3: authentication failed, 4: incomplete] (optional).
* **currentPage**: (int) The current page number (optional).
* **pageSize**: (int) The number of results per page (default is 10, maximum is 1000).

#### Response Structure

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1,                  // (number: current page number)
        "size": 10,                         // (number: number of results per page)
        "total": 100,                       // (number: total number of results)
        "data": [                           // (array: list of merchant accounts)
            {   
                "merchantId": 1,            // (number: id of the merchant)
                "fiat": "MXN",               // (string: name of the fiat currency)
                "balance": "100.00",         // (decimal: amount of Merchant balance)
                "status": 1,                 // (enum: status of the merchant [1: authenticating, 2: normal, 3: authentication failed, 4: incomplete])   
                "paymentId": 58,             // (number: ID of the payment configuration)
                "paymentMethodName": "Automated SPEI - Arcus", // (string: name of the payment method)
                "createTime": "1737452292000", // (string: timestamp of the create time (milliseconds))
                "updateTime": "1737452344000" // (string: timestamp of the update time (milliseconds))
                
                
                //-------------------------------
                // Added limit fields from Java
                //-------------------------------              

                "monthBuyLimit": "0",          // (decimal: monthly buy fiat limit)
                "monthBuyUsed": "0",           // (decimal: monthly buy fiat used amount)
                "monthSellLimit": "0",         // (decimal: monthly sell fiat limit)
                "monthSellUsed": "0",          // (decimal: monthly sell fiat used amount)               

                "failReason": ""               // (string: reason of failure, if any)
                
            }
        ]
    }
}
```

**Example Response**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1,
        "size": 10,
        "total": 100,
        "data": [
            {
                "merchantId": 1,
                "fiat": "MXN",
                "balance": "100.00",
                "status": 2,
                "buyAmountLimit": "0",
                "buyAmountUsed": "2000.00",
                "sellAmountLimit": "10000.00",
                "sellAmountUsed": "0",
                "paymentId": 58, 
                "paymentMethodName": "Automated SPEI - Arcus",
                "createTime": "1737452292000",
                "updateTime": "1737452344000",
              
                "monthBuyLimit": "0", 
                "monthBuyUsed": "0", 
                "monthSellLimit": "0", 
                "monthSellUsed": "0", 
            
                "failReason": "",
            },
            {
                "merchantId": 2,
                "fiat": "ARS",
                "balance": "500.00",
                "status": 1,
                "buyAmountLimit": "1000.00",
                "buyAmountUsed": "500.00",
                "sellAmountLimit": "20000.00",
                "sellAmountUsed": "1000.00",
                "paymentId": 63, 
                "paymentMethodName": "Automated Bank Transfer",
                "createTime": "1737452292001",
                "updateTime": "1737452344001",
                
                "monthBuyLimit": "0", 
                "monthBuyUsed": "0", 
                "monthSellLimit": "0", 
                "monthSellUsed": "0", 
            
                "failReason": "",
            }
            // Additional merchant accounts may be included
        ]
    }
}
```

#### Notes

* The `currentPage` field indicates the page of results currently being returned.
* The `size` field shows the number of results returned per page.
* The `total` field indicates the total number of merchant accounts available based on the query.
* Each account object includes relevant details such as merchant ID, fiat currency, balance, status, limits, and timestamps for creation and updates.
