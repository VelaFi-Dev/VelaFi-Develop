---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/payment-method/add-payment-method
---

# Add Payment Method

This API allows you to add a new payment method for a merchant.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/payments`
* **Authorization Required**: Yes

#### Request Body Parameters

The request body should include the following fields:

```json
{
  "merchantId": 0,         // (number: id of the merchant id)
  "paymentId": 0,          // (number: payment ID)
  "country": "",            // (string: name of the country)
  "fiat": "",               // (string: name of the fiat currency)
  "realName": "",           // (string: real name of the account holder)
  "fieldJson": {            // (object: field JSON of the payment template)
       [string]: [string]   // (key-value pairs as per the payment template)
  },
  "remark": ""              // (string: remark about the payment method)
}
```

#### Authorization

This request requires authorization.

#### Response Structure

The response will include the following fields:

```json
{
  "code": 0,                            // (number: response code)
  "msg": "",                             // (string: message)
  "data": {                              // (object: result data)
      "id": 0,                           // (number: user payment ID)
      "status": 0,                       // (number: status [1: valid, 2: authenticating, 3: authentication failed])
      "failReason": ""                   // (string: reason for authentication failure)
  }
}
```

**Example Request (Mexico - MXN)  105: SPEI - FINCO PAY**

```json
{
  "merchantId": 123,
  "paymentId": 105,
  "country": "Mexico",
  "fiat": "MXN",
  "realName": "John Doe",
  "fieldJson": {
      "Account Type":"clabe", //account type enum [clabe: VA account, debit: card account]
      "Account Number": "123456789012345678", //account number   
      "Beneficiary Name": "John Doe", //beneficiary name
      "Bank Code": "" //bank code, Only fill in when the account type is "debit", The list is shown in https://docs.velafi.com/api-reference/payment-method/get-payment-templates#mexico-finco-pay-bank-codes
  },
  "remark": "Preferred payment method"
}
```

**Example Request (Mexico - MXN)  72: SPEI (Tesored)**

```json
{
  "merchantId": 123,
  "paymentId": 72,
  "country": "Mexico",
  "fiat": "MXN",
  "realName": "John Doe",
  "fieldJson": {
      "Account Type":"clabe", //account type enum [clabe: VA account, spei_card: card account]
      "Full Name": "John Doe", //beneficiary name
      "Bank Account Number": "123456789012345678", //account number
      "Bank Code": "" //bank code, Only fill in when the account type is "spei_card", The list is shown in https://docs.velafi.com/api-reference/payment-method/get-payment-templates#mexico-tesored-bank-codes
  },
  "remark": "Preferred payment method"
}
```

**Example Request (Argentina - ARS) 63: CBU/CVU (Momentum)**

```json
{
  "merchantId": 123,
  "paymentId": 63,
  "country": "Argentina",
  "fiat": "ARS",
  "realName": "John Doe",
  "fieldJson": {     
      "CVU/CBU Number": "0000775900000000000041", //cvu/cbu account number, 22 digits
      "CUIT": "20339698693" //cuit, 11 digits
  },
  "remark": "Preferred payment method"
}
```

**Example Request (Argentina - ARS) 137: QR Argentina**

```json
{
    "merchantId": 15123,
    "paymentId": 137,
    "country": "Argentina",
    "fiat": "ARS",
    "realName": "John Doe",
    "fieldJson": {
        "cuit": "123456789", //cuit, 11 digits  
        "cvu/cbu":"123456789" //cvu/cbu account number, 22 digits 
    },
    "remark": "Preferred payment method"
}
```

**Example Request (Colombia - COP)** **68: ACH/PSE**

```json
{
    "merchantId": 15123,
    "paymentId": 58,
    "country": "Colombia",
    "fiat": "COP",
    "realName": "Tom",
    "fieldJson": {
        "Account Type": "cc", //enum: account type[cc: Checking Account, ch: Savings Account, dp:Electronic deposit]
        "Full Name": "Tom", //full name, Maximum length: 300
        "ID Document Type": "cc", //enum: Type of identification document[cc: Citizenship ID, nit: Tax Identification Number, ce: Foreigner ID,  pa: Pasaporte (Passport),  ppt: Temporary Protection Permit,  ti: Identity Card, rc: Civil Registry, te: Foreigner Card, die: Foreign Identification Document, nd: No Document]
        "ID Document Number": "123456789", //Identification number, Maximum length: 300
        "Bank Code": "1007", //Bank Code, The list is shown in https://docs.velafi.com/api-reference/payment-method/get-payment-templates#colombian-bank-codes
        "Bank Account Number": "9876543210" //Bank Account Number, Maximum length: 300
    },
    "remark": "Preferred payment method"
}
```

**Example Request (Brazil - BRL)  90: Pix (Genial)**

```json
{
    "merchantId": 15123,
    "paymentId": 90,
    "country": "Brazil",
    "fiat": "BRL",
    "realName": "Tom",
    "fieldJson": {
        "Pix Type": "EMAIL", //enum: pix type[CPF:11 digits, CNPJ:14 digits, EMAIL:email, PHONE: 10-11 digits, RANDOM_KEY: with "-"]
        "Pix Key": "tom@gmail.com" //pix key, Maximum length: 100
    },
    "remark": "Preferred payment method"
}
```

**Example Request (Brazil - BRL)  135: Pix (a55)**

```json
{
    "merchantId": 15123,
    "paymentId": 135,
    "country": "Brazil",
    "fiat": "BRL",
    "realName": "Tom",
    "fieldJson": {
        "Pix Type": "EMAIL", //enum: pix type[CPF:11 digits, CNPJ:14 digits, EMAIL:email, PHONE: 10-11 digits, RANDOM_KEY: with "-"]
        "Pix Key": "tom@gmail.com" //pix key, Maximum length: 100
    },
    "remark": "Preferred payment method"
}
```



**Example Request (Peru - PEN)  95: Bank Transfer**

```json
{
    "merchantId": 15123,
    "paymentId": 90,
    "country": "Peru",
    "fiat": "PEN",
    "realName": "Tom",
    "fieldJson": {       
        "Bank Name": "01", //bank code, The list is shown in https://docs.velafi.com/api-reference/payment-method/get-payment-templates#peru-bank-codes
        "Account Type": "00", //enum: account type[00:CORRIENTE, 01:AHORROS]
        "Account Number": "1110333710152", //account number
        "CCI Number": "", //Payer's intermediary account(20 digits), When the Bank Name is not one of the four major banks(01-BCP, 02-Interbank, 03-BBVA, 04-Scotiabank), it must be filled in.
        "Email": "tom@gmai.com", //email
        "Identification Type": "00", //identification type[00:CC (8 digits), 01:CE (>9 digits), 02:Tax ID (11 digits), 03:PAS (>9 digits), 04:PAR, 05:LMI]
        "Identification Number": "12345678", //identification number
        "Name": "Tom", //user name
        "Phone Number": "975728895" //user phone number (9 digits)
    },
    "remark": "Preferred payment method"
}
```

**Example Request (United States - USD) 111:Wire (Virtual - CRB)**

```json
{
    "merchantId": 15123,
    "paymentId": 111,
    "country": "United States",
    "fiat": "USD",
    "realName": "Tom",        
    "fieldJson": {       
        "Account Owner Type": "individual", //account type[individual/business]
        "Bank Name": "Bank of Nowhere", //bank name
        "Beneficiary Name": "Tom", //name
        "Email": "tom@gmail.com", //email
        "National code": "1", //International area code for mobile phones
        "Phone Number": "123456", //phone number
        "Account Number": "11223344556663", //account number
        "Routing Number": "123456795", //routing Number
        "Street Line1": "street example", //street
        "City": "New City", //city
        "State": "AL", //state code
        "Postal Code": "123456", //postal code
        "Purpose Of Payment": "invoice_payments" //purpose of payment[invoice_payments/payment_for_services/payment_for_imported_goods/travel_services/transfer_to_own_account/repayment_of_loans/payroll/payment_of_property_rental/information_service_charges/advertising_and_public_relations/royalty_and_ip_fees/financial_service_fees/advisory_and_consulting_fees/representative_office_expenses/tax_payment/transportation_fees/construction_costs/insurance_premium/offline_goods_trade/insurance_claims/remittance_to_family_or_friends/education_expenses/medical_treatment/donations/currency_exchange/advance_payment_for_goods/merchant_settlement/repatriation_fund_settlement]
    },
    "remark": "Preferred payment method"
}
```



**Example Request 120/121/125/126: Wire (CPN)/CIPS (CPN)/BANK-TRANSFER(CPN)/PESONET(CPN)**

```json
{
    "merchantId": 15123,
    "paymentId": 120,
    "country": "United States",
    "fiat": "USD",
    "realName": "Tom",
    "fieldJson": { 
        "beneficiaryName": "Tom", //name
				"country": "US", //nationality
				"stateProvince": "US-AK", //country and province code of the address location
				"city": "Alaska", //city
				"street": "789 street", //street
				"postalCode": "10001", //postal code
				"dateOfBirth": "1990-01-01", //Date of Birth or Date of Registration				
				"idNumber": "123456", //ID Number
			  "idExpirationDate": "2099-01-01", //expiration date
				"useCase": "B2B", //usd case
				"reasonForPayment": "PMT001", //reason for payment
				"bankName": "Bank of Nowhere", //bank name
				"bankCountry": "US", //bank country 
				"swiftCode": "NACKUSAK001", //swift code
				"accountNumber": "123456" //account number      
    },
    "remark": "Preferred payment method"
}
```

**Example Request  (Hong Kong - HKD) 122: FPS (CPN)**

```json
{
    "merchantId": 15123,
    "paymentId": 122,
    "country": "Hong Kong",
    "fiat": "HKD",
    "realName": "Tom",
    "fieldJson": { 
       	"beneficiaryName": "Tom", //name
				"country": "HK", //nationality
				"stateProvince": "HK-HK", //country and province code of the address location
				"city": "Hong Kong", //city
				"street": "789 street", //street
				"postalCode": "999077", //postal code
				"dateOfBirth": "1990-01-01", //Date of Birth or Date of Registration	
				"idNumber": "123456", //ID Number
				"idExpirationDate": "2099-01-01", //expiration date
				"useCase": "B2B", //usd case
				"reasonForPayment": "PMT001", //reason for payment
				"recipientEmail": "tom@gmail.com", //recipient email
				"recipientPhoneNumber": "123456", //recipient phone number
				"fpsId": "123321", //fps id
				"bankCode": "999077", //bank code
				"accountNumber": "123456"  //account number       
    },
    "remark": "Preferred payment method"
}
```

**Example Request (Hong Kong - HKD) 123: CHATS (CPN)**

```json
{
    "merchantId": 15123,
    "paymentId": 123,
    "country": "Hong Kong",
    "fiat": "Hong Kong",
    "realName": "Tom",
    "fieldJson": { 
       	"beneficiaryName": "Tom", //name
				"country": "HK", //nationality
				"stateProvince": "HK-HK", //country and province code of the address location
				"city": "Hong Kong", //city
				"street": "789 street", //street
				"postalCode": "999077", //postal code
				"dateOfBirth": "1990-01-01", //Date of Birth or Date of Registration	
				"idNumber": "123456", //ID Number
				"idExpirationDate": "2099-01-01", //expiration date
				"useCase": "B2B", //usd case
				"reasonForPayment": "PMT002", //reason for payment
				"bankCode": "999077", //bank code
				"bankName": "BANK", //bank name
				"swiftCode": "999077", //swift code
				"accountNumber": "123456", //account number   
				"recipientCity": "Hong Kong", //recipient city
				"recipientAddressStreet": "789 street", //recipient address street
				"recipientAddressCity": "Hong Kong", //recipient address city
				"recipientAddressCountry": "HK", //recipient address country
				"recipientAddressStateProvince": "HK-HK", //recipient address postal code
				"recipientAddressPostalCode": "999077" //recipient address postal code 
    },
    "remark": "Preferred payment method"
}
```

**Example Request (Europe - EUR) 124: SEPA(CPN)**

```json
{
    "merchantId": 15123,
    "paymentId": 124,
    "country": "Estonia",
    "fiat": "EUR",
    "realName": "Tom",
    "fieldJson": { 
       	"beneficiaryName": "Tom", //name
				"country": "EE", //nationality
				"stateProvince": "EE-37", //country and province code of the address location
				"city": "Estonia", //city
				"street": "789 street", //street
				"postalCode": "51004", //postal code
				"dateOfBirth": "1990-01-01", //Date of Birth or Date of Registration	
				"idNumber": "123456", //ID Number
				"idExpirationDate": "2099-01-01", //expiration date
				"useCase": "B2B", //usd case
				"reasonForPayment": "PMT001", //reason for payment
				"bankName": "BANK", //bank name
				"bankCountry": "EE", //bank country 
				"swiftCode": "NACKEE37001", //swift code
				"accountNumber": "123456" //account number   
    },
    "remark": "Preferred payment method"
}
```

**Example Request (United States - USD) 127: FEDWIRE(CPN)**

```json
{
    "merchantId": 15123,
    "paymentId": 127,
    "country": "France",
    "fiat": "EUR",
    "realName": "Tom",
    "fieldJson": { 
       	"beneficiaryName": "Tom", //name
				"country": "US", //nationality
				"stateProvince": "US-AK", //country and province code of the address location
				"city": "Anchorage", //city
				"street": "789 street", //street
				"postalCode": "99508", //postal code
				"dateOfBirth": "1990-01-01", //Date of Birth or Date of Registration	
				"idNumber": "123456", //ID Number
				"idExpirationDate": "2099-01-01", //expiration date
				"useCase": "B2B", //usd case
				"reasonForPayment": "PMT001", //reason for payment
				"bankName": "Bank of America", //bank name
				"bankCountry": "US", //bank country 
				"accountNumber": "12345678", //account number   
				"routingNumber": "11326", //routing number
				"recipientCity": "Anchorage", //recipient city
				"recipientAddressStreet": "789 street", //recipient address street
				"recipientAddressCity": "Anchorage", //recipient address city
				"recipientAddressCountry": "US", //recipient address country
				"recipientAddressStateProvince": "US-AK", //recipient address postal code
				"recipientAddressPostalCode": "90210" //recipient address postal code 
    },
    "remark": "Preferred payment method"
}
```

#### Example Response

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
      "id": 456,
      "status": 1,
      "failReason": ""
  }
}
```

#### Notes

* The `fieldJson` object should match the required fields for the specified payment method template.
* Ensure that valid authorization tokens are included in the request headers for successful execution.
