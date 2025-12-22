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

#### Example Request (Mexico - MXN)  58: Automated SPEI - Arcus

```json
{
  "merchantId": 123,
  "paymentId": 58,
  "country": "Mexico",
  "fiat": "MXN",
  "realName": "John Doe",
  "fieldJson": {
      "Cuenta CLABE": "123456789012345678", //clabe number
      "Banco": "Banamex", //bank name
      "Beneficiary Name": "John Doe" //beneficiary name
  },
  "remark": "Preferred payment method"
}
```

#### Example Request (Mexico - MXN)  105: SPEI - FINCO PAY

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

#### Example Request (Argentina - ARS)

```json
{
  "merchantId": 123,
  "paymentId": 63,
  "country": "Argentina",
  "fiat": "ARS",
  "realName": "John Doe",
  "fieldJson": {
      "Bank Name": "Banco Galicia",
      "CVU Number": "0000775900000000000041",
      "CUIT": "20339698693"
  },
  "remark": "Preferred payment method"
}
```

**Example Request (Colombia - COP)**

```json
{
    "merchantId": 15123,
    "paymentId": 58,
    "country": "Colombia",
    "fiat": "COP",
    "realName": "Tom",
    "fieldJson": {
        "Account Type": "cc", //enum: account type[cc: Checking Account, ch: Savings Account, dp:Electronic deposit]
        "Full Name": "Tom", //full name
        "ID Document Type": "cc", //enum: Type of identification document[cc: Citizenship ID, nit: Tax Identification Number, ce: Foreigner ID,  pa: Pasaporte (Passport),  ppt: Temporary Protection Permit,  ti: Identity Card, rc: Civil Registry, te: Foreigner Card, die: Foreign Identification Document, nd: No Document]
        "ID Document Number": "123456789", //Identification number
        "Bank Code": "1007", //Bank Code, The list is shown in https://docs.velafi.com/api-reference/payment-method/get-payment-templates#colombian-bank-codes
        "Bank Account Number": "9876543210" //Bank Account Number
    },
    "remark": "Preferred payment method"
}
```

**Example Request (Brazil - BRL)**

```json
{
    "merchantId": 15123,
    "paymentId": 90,
    "country": "Brazil",
    "fiat": "BRL",
    "realName": "Tom",
    "fieldJson": {
        "Pix Type": "EMAIL", //pix type[CPF:11 digits, CNPJ:14 digits, EMAIL:email, PHONE: 10-11 digits, RANDOM_KEY: with "-"]
        "Pix Key": "tom@gmail.com" //pix key      
    },
    "remark": "Preferred payment method"
}
```

**Example Request (Peru - PEN)**

```json
{
    "merchantId": 15123,
    "paymentId": 90,
    "country": "Peru",
    "fiat": "PEN",
    "realName": "Tom",
    "fieldJson": {       
        "Bank Name": "01", //bank code, The list is shown in https://docs.velafi.com/api-reference/payment-method/get-payment-templates#peru-bank-codes
        "Account Type": "00", //account type[00:CORRIENTE, 01:AHORROS]
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

**Example Request (United States - USD)**

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
        "Email": "tom@gmail.com", //emial
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

**Example Request (Hong Kong - USD)**

```json
{
    "merchantId": 15123,
    "paymentId": 115,
    "country": "Hong Kong",
    "fiat": "USD",
    "realName": "Tom",
    "fieldJson": {       
        "Account Owner Type": "individual", //account type[individual/business]
        "Bank Name": "Bank of Nowhere", //bank name
        "Beneficiary Name": "Tom", //name
        "Date of birth or formation": "2020-01-01", //date of birth or formation
        "Id Number": "123456", //id number
        "Account Number": "123456789", //account number
        "Swift Code": "ICEKHKHK001", //swift code
        "Street Line1": "789 street", //street
        "City": "Hong Kong", //city
        "State": "HK", //state code
        "Postal Code": "999077", //postal code
        "Purpose Of Payment": "invoice_payments" ////purpose of payment[invoice_payments/payment_for_services/payment_for_imported_goods/travel_services/transfer_to_own_account/repayment_of_loans/payroll/payment_of_property_rental/information_service_charges/advertising_and_public_relations/royalty_and_ip_fees/financial_service_fees/advisory_and_consulting_fees/representative_office_expenses/tax_payment/transportation_fees/construction_costs/insurance_premium/offline_goods_trade/insurance_claims/remittance_to_family_or_friends/education_expenses/medical_treatment/donations/currency_exchange/advance_payment_for_goods/merchant_settlement/repatriation_fund_settlement]
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
