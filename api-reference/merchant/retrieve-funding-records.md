---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/retrieve-funding-records
---

# Retrieve Funding Records

This endpoint provides a detailed history of your Pending Fund activity, including deposits, usage, and withdrawals. It helps you maintain full transparency and traceability over your fund operations.



**Endpoint Information**

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Method:** GET
* **Request Path:** `/v2/merchant/funding/records`
* **Authorization Required:** Yes

**Query Parameters**

The following query parameters can be used:

* **startTime:** (long) The start time (in milliseconds).
* **endTime:** (long) The end time (in milliseconds).
* **merchantId:** (int) The ID of the merchant.
* **fiat:** (string) The fiat currency.
* **type:** (string) The transaction type. Options include:
  * `ALL` (default)
  * `DEPOSIT`: The addition of the funding record
  * `WITHDRAW`: The claim of the funding record
  * `BUY_CRYPTO`: The purchase of cryptocurrency
  * `REFUND`: The refund of the funding record
  * `TRANSFER_IN`: The internal transfer of funds between merchants into the account
  * `TRANSFER_OUT`: The internal transfer of funds between merchants out of the account
* **status:** (int) The status. Options include:
  * `0` (all, default)
  * `1`: pending
  * `2`: completed
  * `3`: canceled
* **clientId:** (string) The ID of the client.
* **currentPage:** (int) The current page number (default is 1).
* **pageSize:** (int) The number of results per page (default is 10, maximum is 1000).

**Response Structure**

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1,         // (number: current page number)
        "size": 10,               // (number: number of results per page)
        "total": 100,             // (number: total number of results)   
        "data": [                 // (array: list of funding records)
            {
                "id": "1123123123",     // (number: ID of the funding)               
                "merchantId": 3,      // (number: ID of the merchant)
                "merchantName": "Rrturo Tellez", // (string: name of the merchant)
                "fiat": "MXN",         // (string: name of the fiat currency) 
                "totalAmount": 22.00,  // (decimal: total fiat amount)
                "amount": 20.00,       // (decimal: actual fiat amount)
                "fee": 2.00,           // (decimal: amount of the fee)
                "userPaymentId": 91,   // (number: ID of the user payment method) 
                "type": "DEPOSIT",     // (enum: transaction type)
                "status": 1,           // (enum: status [1: pending, 2: completed, 3: canceled])               
                "createTime": "1737452292000", // (string: timestamp of creation in milliseconds)
                "updateTime": "1737452344000"  // (string: timestamp of update in milliseconds)
            }
            // Additional funding records may be included
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
                "txId": 1123123123,         
                "merchantId": 3,
                "merchantName": "Rrturo Tellez",
                "fiat": "MXN", 
                "totalAmount": 22.00, 
                "amount": 20.00, 
                "fee": 2.00,
                "userPaymentId": 91,
                "type": "DEPOSIT",
                "status": 1, 
                "createTime": "1737452292000", 
                "updateTime": "1737452344000"
            }
            // Additional funding records may be included
        ]
    }
}
```

#### Notes

* The `currentPage` field indicates the page of results currently being returned.
* The `size` field shows the number of results returned per page.
* The `total` field indicates the total number of funding records available based on the query.
* Each transaction object includes relevant details such as transaction ID, merchant ID, merchant name, fiat currency, total amount, actual amount, fee, type, status, and timestamps for creation and updates.
