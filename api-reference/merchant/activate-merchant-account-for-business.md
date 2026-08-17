# Activate Merchant Account (For Business)

This endpoint is used to activate a merchant's fiat currency payment account. Supported currencies include MXN, ARS, COP, BRL,PEN,USD, and EUR. Once activated, merchants can send and receive funds through local banking channels with increased flexibility and efficiency.

* Each merchant will receive dedicated account details (e.g., ARS accounts include CVU number / CUIT for Argentina).
* Merchants can deposit funds via wire transfer; VelaFi will automatically reconcile the transaction and credit the merchant’s account balance.
* Both business and individual account types are supported, enabling broad use across various payment scenarios.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/merchant/accounts`
* **Authorization Required**: Yes



#### **Example Requests (For Business)**

**For MXN Account 01 (Mexico)**

Supported payment methods: SPEI (Finco Pay)

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "CLABE - FINCO PAY" //(required, string: trench [CLABE - FINCO PAY])    
}
```

**or MXN Account 02 (Mexico)**

Supported payment methods: SPEI (Tesored)

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "CLABE - TESORED" //(required, string: trench [CLABE - TESORED])    
}
```

**For ARS Account 01 (Argentina)**

Supported payment methods: CBU/CVU (Momentum)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "ARS", // (required, string: name of the fiat currency [ARS])
    "trench": "CVU - Momentum" //(required, string: trench [CVU - Momentum]) 
}
```

**For ARS Account 02 (Argentina)**

Supported payment methods: 3.0 Transfer (QR)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "ARS", // (required, string: name of the fiat currency [ARS])
    "trench": "QR Argentina", //(required, string: trench [QR Argentina]) 
    "fieldList":{
        "cuit": "123456789" //(optional,string: Additional arbitrary metabata to attach to the transaction.)
    }   
}

```

**For COP Account (Colombia)**

Supported payment methods: PSE, ACH, Bre-B

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "COP", // (required, string: name of the fiat currency [COP])
    "trench": "COP Account" //(required, string: trench [COP Account]) 
}
```

**For BRL Account 01 (Brazil)**

Supported payment methods: Pix (Genial)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "BRL", // (required, string: name of the fiat currency [BRL])
    "trench": "BANCO GENIAL" //(required, string: trench [BANCO GENIAL])
}
```

**For BRL Account 02 (Brazil)**

Supported payment methods:  Pix - Woovi

Contact the business department to activate this channel offline.



**For PEN Account (Peru)**

Supported payment methods: Bank Transfer

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "PEN", // (required, string: name of the fiat currency [PEN])
    "trench": "PEN Account" //(required, string: trench [PEN Account]) 
}
```

**For EUR/USD Account 01**

Once activated, the EUR account supports both EUR and USD transactions. Supported payment methods: ACH\_push, ACH\_Virtual Account, WIRE, WIRE\_Virtual Account, SEPA

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "EUR", // (required, string: name of the fiat currency [USD/EUR]) 
    "trench": "Lead Bank", //(required, string: trench [Account_Lead Bank/Wire - Standard Charted Bank])    
    "callbackUri": "https://localhost/home", //(string: callback address after accepting the agreement)
    "fieldList": { // List of channel fields
        "email": "rturo@gmail.com", // (optional, string: Email, if the merchant information is not provided, it must be filled in)
        "companyName": "CAPITAL SA COCOS", // (required, string: Company Name)        
    }
}
```

**For USD/CNY/HKD/EUR/SGD/NGN/PHP** **Account 03**

Supported payment methods: Wire (CPN), CIPS (CPN), FPS (CPN), CHATS (CPN), SEPA(CPN), BANK-TRANSFER(CPN), PESONET(CPN), FEDWIRE(CPN)<br>

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "USD", // (required, string: name of the fiat currency [PEN])
    "trench": "Circle Payment Network", //(required, string: trench)    
}
```



#### **Example Responses**

**Example Response (MXN/ARS/COP/BRL/PEN)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "fiat": "USD",
        "status": 0,
        "verifyLink": "https://verify-sandbox.aiprise.com/?business_onboarding_session_id=xxx",
        "failReason": ""        
    }
}
```

**Example Response (USD / EUR)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "fiat": "USD",
        "status": 4,
        "verifyLink": "https://www.vealfi-test.com/business/channel/verify?token=12ceff08f9621808b5a573972cdfb10f",
        "failReason": ""        
    }
}
```

#### Notes

* Ensure that all fields in the request body are filled out correctly to facilitate the activation process.
* Merchants may need to provide additional documentation based on the type of account being activated.
