---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/activate-merchant-account
---

# Activate Merchant Account (For Individual)

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

####

#### **Example Requests (For Individual)**

**For MXN Account 01 (Mexico)**

Supported payment methods: SPEI (Finco Pay)

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "CLABE - FINCO PAY", //(required, string: trench [CLABE - FINCO PAY])     
    "fieldList": { // List of channel fields
        "alias": "rturo_alias", // (required, string: alias)
    }
}
```

**For MXN Account 02 (Mexico)**

Supported payment methods: SPEI (Tesored)

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "CLABE - TESORED", //(required, string: trench [CLABE - TESORED])     
    "fieldList": { // List of channel fields
        "alias": "rturo_alias", // (required, string: alias)
    }
}
```

**For ARS Account 01 (Argentina)**

Supported payment methods: CBU/CVU (Momentum)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "ARS", // (required, string: name of the fiat currency [ARS])
    "trench": "CVU - Momentum", //(required, string: trench [CVU - Momentum]) 
    "fieldList": { // List of channel fields
        "email": "rturo@gmail.com", // (optional, string: Email, if the merchant information is not provided, it must be filled in)
        "cuit": "30708424478", // (required, string: CUIT)
        "name": "COCOS CAPITAL SA", // (required, string: Full Name)
        "alias": "soc.te" // (optional, string: Alias)
    }
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
    "trench": "COP Account", //(required, string: trench [COP Account]) 
    "fieldList": { // List of channel fields
        "alias": "soc.te" // (required, string: Alias)
    }
}
```

**For BRL Account 01 (Brazil)**

Supported payment methods:  Pix (Genial)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "BRL", // (required, string: name of the fiat currency [BRL])
    "trench": "BANCO GENIAL" //(required, string: trench [BANCO GENIAL])    
}
```

**For PEN Account (Peru)**

Supported payment methods: Bank Transfer

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "PEN", // (required, string: name of the fiat currency [PEN])
    "trench": "PEN Account", //(required, string: trench [PEN Account]) 
    "fieldList": { // List of channel fields
        "customerIdentificationType": "00", // (required, string: identification type[00:CC (8 digits), 01:CE (>9 digits), 02:Tax ID (11 digits), 03:PAS (>9 digits), 04:PAR, 05:LMI])
        "customerIdentification": "12345678", // (required, string: identification number)
        "customerName": "Tom", // (required, string: name)
        "lastName": "", // (optional, string: surname, The merchant type must be selected as "Individual" for this field.)
        "customerEmail": "tom@gmai.com", // (required, string: email)
        "customerPhone": "975728895" // (required, string: phone number)       
    }
}
```

**For EUR/USD Account 01**

Once activated, the EUR account supports both EUR and USD transactions. Supported payment methods: ACH (Reference - Lead Bank), ACH (Virtual - Lead Bank), Wire (Reference - Lead Bank), Wire (Virtual - Lead Bank), SEPA (Bridge)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "EUR", // (required, string: name of the fiat currency [USD/EUR]) 
    "trench": "Lead Bank", //(required, string: trench [Lead Bank])     
    "callbackUri": "https://localhost/home", //(string: callback address after accepting the agreement)
    "fieldList": { // List of channel fields
        "email": "rturo@gmail.com", // (optional, string: Email, if the merchant information is not provided, it must be filled in)
        "firstName": "CAPITAL SA", // (required, string: First Name)
        "lastName": "COCOS" // (required, string: Last Name)
    }
}
```

**For USD/CNY/HKD/EUR/SGD/NGN/PHP** **Account 02**

Supported payment methods: Wire (CPN), CIPS (CPN), FPS (CPN), CHATS (CPN), SEPA(CPN), BANK-TRANSFER(CPN), PESONET(CPN), FEDWIRE(CPN)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "USD", // (required, string: name of the fiat currency [PEN])
    "trench": "Circle Payment Network", //(required, string: trench)
    "fieldList": { // List of channel fields
        "accountName": "Tom", // (required, string: account number)
        "nationality": "HK", // (required, string: nationality)
        "idNumber": "123456", // (required, string: identification number)
        "countryStateCode": "HK-HK", // (required, string: country and province code of the address location)
        "city": "Hong Kong", // (required, string: city)
        "street": "street 789", // (required, string: street)
        "postalCode": "123456", // (required, string: postal code)
        "dateOfBirth": "1990-01-01", // (required, string: date of birth)
        "phoneNumber": "123456" // (required, string: phone number)       
    }
}
```



**Example Responses**

**Example Response (MXN/ARS/COP/BRL/PEN)**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "fiat": "MXN",
        "status": 1,
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
