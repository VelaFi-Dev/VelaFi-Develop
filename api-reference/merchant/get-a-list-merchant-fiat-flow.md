# Get a List Merchant Fiat Flow

This endpoint will provide you with your fiat transaction history.



**Endpoint Information**

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Method:** GET
* **Request Path:** `/v2/merchant/fiat/flows`
* **Authorization Required:** Yes

**Query Parameters**

The following query parameters can be used:

* **startTime:** (long) The start time (in milliseconds).
* **endTime:** (long) The end time (in milliseconds).
* **merchantId:** (int) The ID of the merchant.
* **fiat:** (string) The fiat currency.
* **txId:** (long) The ID of the tx.
* **flowType:** (string) The transaction type. Options include:
  * `ALL` (default)
  * `DEPOSIT`: The addition of the funding record
  * `WITHDRAW`: The claim of the funding record
  * `WITHDRAW_ROLLBACK`: The claim of the funding record rollback
  * `BUY_CRYPTO`: The purchase of cryptocurrency
  * `BUY_CRYPTO_ROLLBACK`: The purchase of cryptocurrency rollback
  * `REFUND`: The refund of the funding record
  * `REFUND_ROLLBACK`: The refund of the funding record rollback
  * `TRANSFER_IN`: The internal transfer of funds between merchants into the account
  * `TRANSFER_OUT`: The internal transfer of funds between merchants out of the account
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
                "id": 282,         // (number: ID of the fiat flow)                  
                "merchantId": 3,   // (number: ID of the merchant)
                "txId": "573901321954934784", // (number: ID of the funding) 
                "category": "TRADE",          // (enum: flow type[TRADE/FEE/TRANSFER])
                "flowType": "DEPOSIT",        // (enum: flow type[BUY_CRYPTO/BUY_CRYPTO_ROLLBACK/REFUND/REFUND_ROLLBACK/DEPOSIT/WITHDRAW/WITHDRAW_ROLLBACK/TRANSFER_IN/TRANSFER_OUT])
                "fiat": "MXN",                // (string: name of the fiat currency) 
                "changed": 105.61,            // (decimal: changed fiat amount)
                "total": 37042.07,            // (decimal: The changed balance)
                "extId": "573901321434841088",  //(string: ID of the ext)
                "createTime": "1737452292000"   // (string: timestamp of creation in milliseconds)
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
                "id": 282,                      
                "merchantId": 3,  
                "txId": 573901321954934784,
                "category": "TRADE",   
                "flowType": "DEPOSIT", 
                "fiat": "MXN",        
                "changed": 105.61,    
                "total": 37042.07,    
                "extId": "573901321434841088", 
                "createTime": "1737452292000"
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
