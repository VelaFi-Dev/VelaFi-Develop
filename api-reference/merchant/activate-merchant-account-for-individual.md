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

**For MXN Account 1**

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "ARCUS FI", //(required, string: trench [ARCUS FI]) 
    "fieldList": { // List of channel fields
        "email": "rturo@gmail.com", // (optional, string: Email, if the merchant information is not provided, it must be filled in)
        "idNoType": "CURP", //(required, enum: type of identification document [CURP/RFC])
        "idNo": "MACM000502IR6",//(required, string: identity number)
        "cardIssueDate": "2019-06-01", // (required, string: Card Issue Date (yyyy-MM-dd))
        "cardExpireDate": "2029-06-01", // (required, string: Card Expiry Date (yyyy-MM-dd))
        "address": "Celle Lagu Wenner 50", // (required, string: Address)
        "city": "Ciudad de Mexico", // (required, string: City)
        "state": "CMX", // (required, string: State)
        "zipCode": "09060", // (required, string: Zip Code)
        "phone": "35580481683", // (required, string: Phone)
        
        "companyName": "Rrturo Tellez", // (string: Company Name, required if merchantType is BUSINESS)
        "aliasName": "Rrturo", // (string: Alias Name, required if merchantType is BUSINESS)
        "companyType": "SC", // (string: Company Type, required if merchantType is BUSINESS)
        "incorporationDate": "2019-02-01", // (string: Incorporation Date (yyyy-MM-dd), required if merchantType is BUSINESS)
    
        "birthday": "1988-07-02", // (string: Birthday (yyyy-MM-dd), required if merchantType is INDIVIDUAL)
        "name": "Tellez", // (string: Name, required if merchantType is INDIVIDUAL)
        "fatherSurname": "Rrturo", // (string: Father's Surname, required if merchantType is INDIVIDUAL)
        "motherSurname": "" // (string: Mother's Surname, required if merchantType is INDIVIDUAL)
    }
}
```

**For MXN Account 2**

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "FINCO PAY", //(required, string: trench [FINCO PAY])     
    "fieldList": { // List of channel fields
        "alias": "rturo_alias", // (required, string: alias)
    }
}
```



**For ARS Account (Argentina)**

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "ARS", // (required, string: name of the fiat currency [ARS])
    "fieldList": { // List of channel fields
        "email": "rturo@gmail.com", // (optional, string: Email, if the merchant information is not provided, it must be filled in)
        "cuit": "30708424478", // (required, string: CUIT)
        "name": "COCOS CAPITAL SA", // (required, string: Full Name)
        "alias": "soc.te" // (optional, string: Alias)
    }
}
```

**For COP Account (Colombia)**

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "COP", // (required, string: name of the fiat currency [COP])
    "fieldList": { // List of channel fields
        "alias": "soc.te" // (required, string: Alias)
    }
}
```

**For BRL Account (Brazil)**

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "BRL", // (required, string: name of the fiat currency [BRL])   
}
```

**For PEN Account (Peru)**

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "PEN", // (required, string: name of the fiat currency [PEN])
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

**For EUR/USD Account 1**

After the EUR currency account is activated, it can be used for both EUR and USD transactions.

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "EUR", // (required, string: name of the fiat currency [USD/EUR]) 
    "trench": "Account_Lead Bank", //(required, string: trench [Account_Lead Bank/Wire - Standard Charted Bank]) 
    "fieldList": { // List of channel fields
        "email": "rturo@gmail.com", // (optional, string: Email, if the merchant information is not provided, it must be filled in)
        "companyName": "CAPITAL SA COCOS", // (string: Company Name, required if merchantType is BUSINESS)
        "firstName": "CAPITAL SA", // (string: First Name, required if merchantType is INDIVIDUAL)
        "lastName": "COCOS" // (string: Last Name, required if merchantType is INDIVIDUAL)
    }
}
```

**For USD Account 2**

```json
{
  "merchantId": "15126673", // (required, number: id of the merchant)
  "fiat": "USD", // (required, string: name of the fiat currency [USD])
  "trench": "Wire - Standard Charted Bank", //(required, string: trench [Account_Lead Bank/Wire - Standard Charted Bank]) 
  "callbackUri": "https://localhost/home", //(string: callback address after accepting the agreement)
  "fieldList": { // List of channel fields  
    "personalInfo": { // Personal information (required when when Merchant Type INDIVIDUAL)
      "firstName": "tom",                    // First name (pinyin or English)(required)
      "lastName": "fr",                     // Last name (pinyin or English)(required)
      "phone": "+12570000000",         // Personal phone number (with country code)(required)
      "email": "tom@example.com",      // Personal email (required)
      "taxIdentificationNumber": "31010119800000000",  // Personal tax ID/ID card number (required)
      "nationality": "US",                  // Nationality code (China)(required)
      "dateOfBirth": "1980-10-10",          // Date of birth (YYYY-MM-DD)(required), age must be between 18 and 120 years.
      "street1": "example street1",       // Street address (required)
      "street2": "",                       // Street address 2
      "city": "New City",                       // City (required)
      "state": "AZ",                        // Province/State code (required)
      "postcode": "901203",                 // Postal code (required)
      "countryAbbr": "US",                  // Country code (required)
      "idType": "1",                        // ID type [1:ID card, 2:Driver's license, 3:Passport/Residence permit](required)
      "idNumber": "31010119800000000",     // ID number (required)
      "govIdCountryAbbr": "US",             // ID issuing country (required)
      "govIdFrontUrl": "user-654321/id-front.jpg",  // ID front side (required), size between 10KB - 3MB, Upload File endpoint: /v2/base/file/upload   
      "govIdBackUrl": "user-654321/id-back.jpg"     // ID back side (required), size between 10KB - 3MB, Upload File endpoint: /v2/base/file/upload  
    },
    "personalQuestionnaireInfo": {   // Personal questionnaire information (required when merchantType=1)
      "actingAsIntermediary": false,        // Acting as intermediary (false=No)(required)
      "employmentStatus": "employed",      // Employment status (required)[employed/homemaker/retired/self_employed/student/unemployed]
      "expectedMonthlyPayments": "5000_9999",    // Expected monthly transaction volume (USD)(required)[0_4999/5000_9999/10000_49999/50000_plus]
      "purposeOfAccount": "charitable_donations",  // Account purpose (required)[charitable_donations/ecommerce_retail_payments/investment_purposes/operating_a_company/other/payments_to_friends_or_family_abroad/personal_or_living_expenses/protect_wealth/purchase_goods_and_services/receive_payment_for_freelancing/receive_salary]
      "occupation": "132011",   // Occupation (required), see list below: occupation codes
      "sourceOfFunds": "salary"   // Source of funds (required)[company_funds/ecommerce_reseller/gambling_proceeds/gifts/government_benefits/inheritance/investments_loans/pension_retirement/salary/sale_of_assets_real_estate/savings/someone_elses_funds]
    }
  }
}

occupation codes:
132011:Accountant and auditor
272011:Actor
152011:Actuary
172021:Agricultural engineer
132031:Budget analyst
412010:Cashier
172041:Chemical engineer
499091:Coin, vending, and amusement machine servicer and repairer
271021:Commercial and industrial designer
273041:Editor
472111:Electrician
434071:File clerk
131111:Management analyst
119199:Manager, other
191040:Medical scientist
195010:Occupational health and safety specialist and technician
27102X:Other designer
2912XX:Other physician
5191XX:Other production worker
519151:Photographic process worker and processing machine operator
211029:Social worker, other
132081:Tax examiner and collector, and revenue agent
151254:Web developer
515111:Prepress technician and worker
273042:Technical writer
172199:Engineer, other
433099:Financial clerk, other
1320XX:Other financial specialist
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
