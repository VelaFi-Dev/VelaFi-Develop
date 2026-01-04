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

Supported payment methods: Automated SPEI - Arcus

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "ARCUS FI", //(required, string: trench [ARCUS FI]) 
}
```

**For MXN Account 02 (Mexico)**

Supported payment methods: SPEI - FINCO PAY

```json
{    
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN])   
    "trench": "FINCO PAY" //(required, string: trench [FINCO PAY])    
}
```

**For ARS Account (Argentina)**

Supported payment methods: Automated Bank Transfer (Argentina)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "ARS" // (required, string: name of the fiat currency [ARS])
}
```

**For COP Account (Colombia)**

Supported payment methods: PSE, ACH, Bre-B

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "COP", // (required, string: name of the fiat currency [COP])
}
```

**For BRL Account (Brazil)**

Supported payment methods: Automated Pix

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "BRL", // (required, string: name of the fiat currency [BRL])   
}
```

**For PEN Account (Peru)**

Supported payment methods: Automated Bank Transfer(Peru)

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "PEN", // (required, string: name of the fiat currency [PEN])
}
```

**For EUR/USD Account 01**

Once activated, the EUR account supports both EUR and USD transactions. Supported payment methods: ACH\_push, ACH\_Virtual Account, WIRE, WIRE\_Virtual Account, SEPA

```json
{
    "merchantId": "15126673", // (required, number: id of the merchant)
    "fiat": "EUR", // (required, string: name of the fiat currency [USD/EUR]) 
    "trench": "Account_Lead Bank", //(required, string: trench [Account_Lead Bank/Wire - Standard Charted Bank]) 
    "fieldList": { // List of channel fields
        "email": "rturo@gmail.com", // (optional, string: Email, if the merchant information is not provided, it must be filled in)
        "companyName": "CAPITAL SA COCOS", // (required, string: Company Name)        
    }
}
```

**For USD Account 02**

Supported payment methods: ACH Account\_Cross River Bank, WIRE Account\_Cross River Bank, Wire - Standard Charted Bank, SWIFT Account\_Cross River Bank

```json
{ 
  "merchantId": "15126673", // (required, number: id of the merchant)
  "fiat": "USD", // (required, string: name of the fiat currency [USD])
  "trench": "Wire - Standard Charted Bank", //(required, string: trench [Account_Lead Bank/Wire - Standard Charted Bank]) 
  "callbackUri": "https://localhost/home", //(string: callback address after accepting the agreement)
  "fieldList": { // List of channel fields  
    "companyInfo": { // Company information (required when Merchant Type BUSINESS)
      "companyName": "Example Corp",         // Full company name (required)
      "companyDescription": "A fintech company providing payment solutions",  // Company description (required)
      "companyIndustry": "FINANCIAL_SERVICES",  // Industry type (Financial Services)(required)
      "email": "contact@example.com",        // Company contact email (required)
      "phoneNumber": "+15551234567",      // Company contact phone number (required)
      "incorporationDate": "2015-06-15",     // Company registration date (required)
      "taxType": "EIN",                      // Tax ID type [EIN/SSN/VAT/TIN/UTR](required)
      "taxId": "123456789",                // Tax ID (required)   
      "website": "https://www.example.com",  // Company website (required)
      "street1": "123 Main St",              // Street address 1 (required)
      "street2": "Suite 100",                // Street address 2
      "city": "New York",                    // City (required)
      "state": "NY",                         // State/Province (required)
      "postcode": "10001",                   // Postal code (required)
      "countryAbbr": "US",                   // Country code (required)
      "legalPresenceUrl": "example-corp/articles.pdf",  // Company registration document (required), size between 10KB - 3MB, Upload File endpoint: /v2/base/file/upload
      "ownershipStructure": "example-corp/ownership.pdf"  // Ownership structure proof (required), size between 10KB - 3MB, Upload File endpoint: /v2/base/file/upload
    },  
    "companyUbosInfo": [ // List of company Ultimate Beneficial Owners (UBO) (required when merchantType=2)
      {
        "personType": "UBO",                // Person type (UBO=Ultimate Beneficial Owner)(required)
        "firstName": "John",                // First name (required)
        "lastName": "Smith",                // Last name (required)
        "email": "john.smith@example.com",  // Email (required)
        "phone": "+15559876543",         // Contact phone number (required)
        "percentageOfOwnership": 0.65,       // Ownership percentage (65%)(required)
        "taxIdentificationNumber": "987654321",  // Personal tax ID (SSN)(required)
        "dateOfBirth": "1980-03-15",        // Date of birth (required), age must be between 18 and 120 years.
        "street": "456 Oak Ave",            // Street address (required)
        "street2": "",                      // Street address 2
        "city": "Brooklyn",                 // City (required)
        "state": "NY",                      // State/Province (required)
        "postcode": "11201",               // Postal code (required)
        "countryAbbr": "US",                // Country code (required)
        "idType": "3",                      // ID type [1:ID card, 2:Driver's license, 3:Passport/Residence permit](required)
        "idNumber": "P12345678",            // ID number (required)
        "govIdCountryAbbr": "US",           // ID issuing country (required)
        "govIdFrontUrl": "john-smith/passport-front.jpg",  // ID front side (required), size between 10KB - 3MB, Upload File endpoint: /v2/base/file/upload     
        "govIdBackUrl": "john-smith/passport-back.jpg",    // ID back side (required), size between 10KB - 3MB, Upload File endpoint: /v2/base/file/upload     
        "hasControl": true,                 // Has control rights (required)
        "hasOwnership": true,               // Has ownership rights (required)
        "hasSigner": true,                  // Is signatory (required), at least one must be true
        "relationshipEstablishedAt": "2015-06-15"  // Relationship establishment date (required)
      }
    ], 
    "companyQuestionnaireInfo": {  // Company questionnaire information (required when merchantType=2)
      "tradeName": "Example Payments",      // Trade name (required)
      "industryType": "cooperative",  // Industry subdivision (required)[cooperative/s_corporation/b_corporation/close_corporation/nonprofit_corporation/general_partnership/limited_partnership/limited_liability_company/other/sole_proprietorship/trust]
      "organizationalChartUrl": "example-corp/org-chart.pdf",  // Organizational chart (required), size between 10KB - 3MB, Upload File endpoint: /v2/base/file/upload
      "estimatedAnnualRevenueUsd": "100000_999999",  // Estimated annual revenue (USD)(required)[0_99999/100000_999999/1000000_9999999/10000000_49999999/50000000_249999999/250000000_plus]
      "expectedMonthlyPaymentsUsd": "500000",   // Expected monthly transaction volume (USD)(required)
      "highRiskActivities": "none_of_the_above",  // High-risk activities[none_of_the_above/adult_entertainment/gambling/hold_client_funds/investment_services/lending_banking/marijuana_or_related_services/money_services/operate_foreign_exchange_virtual_currencies_brokerage_otc/safe_deposit_box_rentals/third_party_payment_processing/weapons_firearms_and_explosives]
      "purposeOfAccount": "charitable_donations",    // Account purpose (required)[charitable_donations/ecommerce_retail_payments/investment_purposes/operating_a_company/other/payments_to_friends_or_family_abroad/personal_or_living_expenses/protect_wealth/purchase_goods_and_services/receive_payment_for_freelancing/receive_salary]
      "sourceOfFunds": "business_loans",       // Source of funds (required)[business_loans/grants/inter_company_funds/investment_proceeds/legal_settlement/owners_capital/pension_retirement/sale_of_assets/sales_of_goods_and_services/tax_refund/third_party_funds/treasury_reserves]
      "transmitsCustomerFunds": true,            // Handles customer funds (required)
      "transmitsCustomerFundsDescription": "We process payments for merchants"  // Funds handling description (required)
    }
  }
}
```

<br>

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
