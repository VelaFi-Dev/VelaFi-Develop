# Get Merchant Virtual Accounts

This endpoint allows you to retrieve information about your VelaFi Virtual Accounts,  With this information, you can pre-load funds into the Pending Fund account in advance. Pre-funding your account enables faster transactions, as you won't need to wait for external transfers to be confirmed at the time of trading.



**Endpoint Information**

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Method:** GET
* **Request Path:** `/v2/merchant/virtual/addfunds`
* **Authorization Required:** Yes

**Query Parameters**

* **merchantId:** (int) The merchant ID.
* **paymentId:** (int) The payment ID. Currently supported payment IDs are：
  * 58 (Automated SPEI - Arcus) - MXN
  * 105 (SPEI - FINCO PAY) - MXN
  * 63 (Automated Bank Transfer (Argentina)) - ARS
  * 68 (PSE) - COP
  * 90 (Automated Pix) - BRL
* **fiat:** (string) Name of the fiat currency. Currently supported currencies are MXN/ARS/COP/BRL.
* **depositAlias**: (string) Alias of the virtual account (optional).
* **currentPage**: (int) The current page number (optional).
* **pageSize**: (int) The number of results per page (default is 10, maximum is 50)  (optional).

**Response Structure**

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1,                  //(number: current page number)
        "size": 10,                        //(number: number of results per page)
        "total": 50,                       //(number: total number of results)
        "record": {  
            "fiat": "MXN",
            "depositAlias": "mx001", //(string: alias)
            "paymentMethodName": "Paypal",  //(string: name of the payment method)
            "status": 2, //(number: The status of the virtual account [1: authenticating, 2: normal, 3: authentication failed])
            "fieldList": {  //(object: list of fields related to the payment method)
                "fieldName1": ["value1", "value2"], // (string: array of values for fieldName1)
                "fieldName2": ["value1", "value2"]  // (string: array of values for fieldName2)
            }
        ]
    }
}

```

**Example Responses**

**Example for Payment ID 58:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1, 
        "size": 10,
        "total": 50,
        "record": {  
            "fiat": "MXN",
            "depositAlias": "alias",
            "paymentMethodName": "Paypal",
            "status": 2,
            "fieldList": {
                "Cuenta CLABE": "706180304649761358",          
                "Beneficiary Name": "Rrturo Tellez"
            }
        ]
    }
}
```

**Example for Payment ID 105:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1, 
        "size": 10,
        "total": 50,
        "record": {  
            "fiat": "MXN",
            "depositAlias": "alias",
            "paymentMethodName": "SPEI - FINCO PAY",
            "status": 2,
            "fieldList": {
                "Cuenta CLABE": "706180304649761358"              
            }
        ]
    }
}
```

**Example for Payment ID 63:**

```json

{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1, 
        "size": 10,
        "total": 50,
        "record": {  
            "fiat": "ARS",
            "depositAlias": "alias",
            "paymentMethodName": "Automated Bank Transfer (Argentina)",
            "status": 2,
            "fieldList": {
                 "CVU number": "0000775900000000000086",
                 "CUIT": "20339698695"             
            }
        ]
    }
}
```

**Example for Payment ID 68:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1, 
        "size": 10,
        "total": 50,
        "record": {  
            "fiat": "COP",
            "depositAlias": "alias",
            "paymentMethodName": "PSE",
            "status": 2,
            "fieldList": {
                 "alias": "alias",
                 "paymentLink": "https://links.velaif.co/zAOCe"       
            }
        ]
    }
}
```

**Example for Payment ID 81/82/83/84:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "fiat": "USD",
        "paymentMethodName": "ACH_push",
        "realName": "",
        "fieldList": {
            "Deposit Message": "BRGJT5PNSZX636P9EC2D",
            "Bank Account Number": "11223344556672",
            "Bank Routing Number": "123456790",
            "Bank Beneficiary Name": "Ventures Inc",
            "Bank Name": "Bank of Nowhere",
            "Bank Address": "1800 North Pole St., Orlando, FL 32803"
        }
    }
}
```

**Example for Payment ID 90:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "currentPage": 1, 
        "size": 10,
        "total": 50,
        "record": {  
            "fiat": "BRL",
            "depositAlias": "alias",
            "paymentMethodName": "Automated Pix",
            "status": 2,
            "fieldList": {
                 "Pix copia e cola": "00020101021126580014br.gov.bcb.pix013865755...",   
                 "Pix QR Code": "https://links.qrcode.co/zAOCe/3471397f291c28d19.png" 
            }
        ]
    }
}
```

#### Notes

* The `paymentMethodName` field indicates the name of the payment method associated with the pending funds.
* The `fieldList` object contains various fields relevant to the payment method, where each key is a field name and the value is an array of associated values.
