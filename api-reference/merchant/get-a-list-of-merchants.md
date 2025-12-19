---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/get-a-list-of-merchants
---

# Get a List of Merchants

This API retrieves a list of merchants based on optional query parameters.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/merchants`
* **Authorization Required**: Yes

#### Query Parameters

* **merchantName**: (string) The name of the merchant (optional).
* **email**: (string) The email of the merchant (optional).
* **status**: (int) The status of the merchant \[-1:all, 1: authenticating, 2: normal(default), 3: authentication failed, 4: incomplete] (optional).
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
        "data": [                           // (array: list of merchants)
            {    
                "merchantId": 1,            // (number: id of the merchant)
                "country": "Mexico",        // (string: name of the country)
                "merchantName": "Rrturo Tellez", // (string: name of the merchant)
                "email": "tellez@gmail.com", // (string: email of the merchant)
                "merchantType": 1,          // (number: merchant type [1: INDIVIDUAL, 2: BUSINESS])
                "status": 1,                 // (enum: status of the merchant [1: authenticating, 2: normal, 3: authentication failed, 4: incomplete])                
                "rejectReason": "",          // (string: reject reason)             
                "upgradeMerchantLimitStatus": 1,   //(enum: status of the upgrade merchant limit[1: authenticating, 2: normal, 3: authentication failed, 4: incomplete])
                "upgradeMerchantLimitRejectReason": "",  // (string: reject reason of upgrade merchant limit)             
                "dayFiatLimit": 25000.0,      // (number: fiat day amount limit)
                "dayFiatUsed": 0.0,           // (number: fiat day amount used) 
                "monthFiatLimit": 25000.0,    // (number: fiat month amount limit)
                "monthFiatUsed": 0.0,         // (number: fiat month amount used)
                "monthCryptoLimit": 15000.0,  // (number: crypto month amount limit)
                "monthCryptoUsed": 0.0,      // (number: crypto month amount used)                                                  
                "remark": "",                // (string: Remark)
                "createTime": "1737452292000", // (string: timestamp of the create time (milliseconds))
                "updateTime": "1737452344000" // (string: timestamp of the update time (milliseconds))
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
                "country": "Mexico",
                "merchantName": "Rrturo Tellez",
                "email": "tellez@gmail.com",
                "merchantType": 1,
                "status": 1,
                "rejectReason": "",
                "upgradeMerchantLimitStatus": 1,
                "upgradeMerchantLimitStatusRejectReason": "",  
                "dayFiatLimit": 25000.0,
                "dayFiatUsed": 0.0,
                "monthFiatLimit": 25000.0,
                "monthFiatUsed": 0.0,
                "monthCryptoLimit": 15000.0,
                "monthCryptoUsed": 0.0,
                "remark": "",
                "createTime": "1737452292000",
                "updateTime": "1737452344000"
            }
            // Additional merchants may be included
        ]
    }
}
```

<br>

#### Notes

* The `currentPage` field indicates the page of results currently being returned.
* The `size` field shows the number of results returned per page.
* The `total` field indicates the total number of merchants available based on the query.
* Each merchant object includes relevant details, such as ID, country, name, email, type, and timestamps for creation and updates.
