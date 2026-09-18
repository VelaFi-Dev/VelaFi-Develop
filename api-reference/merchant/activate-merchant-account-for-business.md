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

```json
{
	"merchantId": "15126673", // (required, number: id of the merchant)
	"fiat": "BRL", // (required, string: name of the fiat currency [BRL])
	"trench": "Pix - Woovi", //(required, string: trench [Pix - Woovi]) 
	"fieldList": {
		"companyInfo": {
			"companyName": "AURORA SANDBOX TECNOLOGIA LTDA.", // (required, string: Company legal name)
			"companyDescription": "test desc", // (required, string: Company Description)
			"countryStateOfIncorporation": "BR-SP", // (required, string: The country of residence - The state/province of residence)
			"website": "1234.com", // (required, string: Website)
			"socialMedia": "social media", // (required, string: Social Media)
			"street1": "Avenida Paulista, 1000", // (required, string: Company address, first line (max 256 chars))
			"street2": "fda", // (Optional, string: Company address, second line.)
			"city": "São Paulo", // (required, string: Company city (max 256 chars).)
			"countryStateCode": "BR-SP", // (required, string: // (required, string: The country of residence - The state/province of residence))
			"postcode": "01310-100", // (required, string: Company postal code (max 256 chars).)
			"reasonForAccountOpening": "ecommerce_retail_payments", // (required, enum: charitable_donations, ecommerce_retail_payments, investment_purposes, other, payments_to_friends_or_family_abroad, payroll, personal_or_living_expenses, protect_wealth, purchase_goods_and_services, receive_payments_for_goods_and_services, tax_optimization, third_party_money_transmission, treasury_management)
			"sourceOfFunds": "grants", // (required, enum: business_loans, grants, inter_company_funds, investment_proceeds, legal_settlement, owners_capital, pension_retirement, sale_of_assets, sales_of_goods_and_services, third_party_funds, treasury_reserves)
			"numberOfEmployees": "11-50", // (required, enum: 1-10, 11-50, 51-200, 201-500, 501-1000, 1001+)
			"estimatedAnnualRevenueUsd": "less_than_100k", // (required, enum: less_than_100k, 100k_to_1m, 1m_to_10m, 10m_to_50m, 50m_to_100m, more_than_100m)
			"estimatedMonthlyVolumeUsd": 10000, // (required, number: Positive integer as string (e.g. "2000"))
			"companyRegistrationNumber": "42731085000167", // (required, string: Company registration number.)
			"taxIdentificationNumberTin": "10000000316452", // (required, string: Company TIN/CNPJ.)
			"taxIdentificationDocumentUrl": "https://files.r2.smallpdf.com/7252fd2f0af7225fd617479a5da271b4.pdf", // (required, string: Certificate of Incorporation, The document must be in PDF format.)
			"certificateOfIncorporationDocumentUrl": "https://files.r2.smallpdf.com/dffcd8e4dfdfa43c55580df208489960.pdf" // (required, string: Tax Identification Document, The document must be in PDF format.)
		},
		"companyUbosInfo": [{
			"personType": "CEO", // (required, string: Website)
			"firstName": "tom", // (required, string: First Name)
			"lastName": "tom", // (Optional, string: Last Name)
			"email": "11@qq.com", // (required, string: UBO contact email)
			"phone": "+14151231234", // (required, string: UBO contact phone)
			"percentageOfOwnership": 1, // (required, string: Percentage of Ownership,0.01 - 1)
			"nationality": "CN", // (required, string: Nationality)
			"taxIdentificationNumber": "432524199612188018", // (required, string: Tax identification number. For BRA a valid CPF is required; for USA a 9-digit number is required.)
			"dateOfBirth": "1999-05-13", // (required, string: YYYY-MM-DD. Minimum age 18.)
			"street1": "789 street", // (required, string: Street address, first line (max 256 chars).)
			"street2": "123", // (required, string: Street address, second line.)
			"city": "Shanghai", // (required, string: City of residence. )
			"countryStateCode": "CN-SH", // (required, string: The country of residence - The state/province of residence)
			"postcode": "200001", // (required, string: Postal code.)
			"idType": "1", // (required, string: gender Only Support [1, 2, 3],[1: ID_CARD,2: DRIVERS ,3: PASSPORT])
			"govIdCountryAbbr": "CN", // (required, string: Gov ID Country)
			"govIdFrontUrl": "https://i.ibb.co/v6nTV8z1/me-id-front-png.jpg" // (required, string: ID Document Front,identification documents accept image/png or image/jpeg)
		}]
	}
}
```



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
