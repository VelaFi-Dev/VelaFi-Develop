---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/get-pending-fund-account
---

# Get Pending Fund Account

This endpoint allows you to retrieve information about your VelaFi Pending Fund account,  With this information, you can pre-load funds into the Pending Fund account in advance. Pre-funding your account enables faster transactions, as you won't need to wait for external transfers to be confirmed at the time of trading.



**Endpoint Information**

* **Request Header:** `X-BH-TOKEN: ******`
* **Request Method:** GET
* **Request Path:** `/v2/merchant/addfunds`
* **Authorization Required:** Yes

**Query Parameters**

* **merchantId:** (int) The merchant ID.
* **paymentId:** (int) The payment ID. Currently supported payment IDs are：
  * 58 (Automated SPEI - Arcus) - MXN
  * 105 (SPEI - FINCO PAY) - MXN
  * 63 (Automated Bank Transfer (Argentina)) - ARS
  * 68 (PSE) - COP
  * 90 (Automated Pix) - BRL
  * 81/82/83/84 (ACH\_push/ACH\_Virtual Accoun/WIRE/WIRE\_Virtual Account) - USD
  * 85 (SEPA) - EUR
  * 95 (Automated Bank Transfer(Peru)) - PEN
* **fiat:** (string) Name of the fiat currency. Currently supported currencies are MXN/ARS/COP/BRL/PEN/USD/EUR.
* **depositAlias**: (string) Alias of the virtual account (optional).
* **amount**: (decimal) The deposit amount. When the currency is PEN, it is mandatory.

**Response Structure**

The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {  
        "paymentMethodName": "Paypal",  // (string: name of the payment method)
        "fieldList": {                   // (object: list of fields related to the payment method)
            "fieldName1": ["value1", "value2"], // (string: array of values for fieldName1)
            "fieldName2": ["value1", "value2"]  // (string: array of values for fieldName2)
        }
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
        "fiat": "MXN",
        "paymentMethodName": "Automated SPEI - Arcus",
        "fieldList": {
             "Cuenta CLABE": "706180304649761358",          
             "Beneficiary Name": "Rrturo Tellez"
        }
    }
}
```

**Example for Payment ID 105:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {  
        "fiat": "MXN",
        "paymentMethodName": "SPEI - FINCO PAY",
        "fieldList": {            
             "Cuenta CLABE": "706180304649761358",           
        }
    }
}
```

**Example for Payment ID 63:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {  
        "fiat": "ARS",
        "paymentMethodName": "Automated Bank Transfer (Argentina)",
        "fieldList": {
             "CVU number": "0000775900000000000086",
             "CUIT": "20339698695"            
        }
    }
}
```

**Example for Payment ID 68:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {   
        "fiat": "COP",
        "paymentMethodName": "PSE",       
        "fieldList": {
            "alias": "soc.ce",
            "paymentLink": "https://links.velaif.co/zAOCe"
        }
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

**Example for Payment ID 85:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "fiat": "EUR",
        "paymentMethodName": "SEPA",
        "realName": "",
        "fieldList": {
            "Deposit Message": "BRGJT5PNSZX636P9EC2D",
            "BIC/Swift Code": "123456790",
            "IBAN": "11223344556672",
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
        "fiat": "BRL",
        "paymentMethodName": "Automated Pix",       
        "fieldList": {  
            "Chave Pix - Random Pix": "09a3b1d1-49d6-4820-bd19-53e7f50ee13c",
            "Pix copia e cola": "00020101021126580014br.gov.bcb.pix013865755...",        
            "Pix QR Code": "https://links.qrcode.co/zAOCe/3471397f291c28d19.png"
        }
    }
}
```

**Example for Payment ID 95:**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {   
        "fiat": "PEN",
        "paymentMethodName": "Automated Bank Transfer(Peru)",       
        "fieldList": {                   
            "paymentLink": "https://links.velaif.co/zEOCb"
        }
    }
}
```

#### Notes

* The `paymentMethodName` field indicates the name of the payment method associated with the pending funds.
* The `fieldList` object contains various fields relevant to the payment method, where each key is a field name and the value is an array of associated values.
