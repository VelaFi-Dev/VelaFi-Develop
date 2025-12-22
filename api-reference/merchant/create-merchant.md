---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/api-reference/merchant/create-merchant
---

# Create Merchant

Create a legal individual or business entity (Merchant) to operate under Velafi's compliance framework.

* Submit your detailed merchant information to initiate the KYC/KYB compliance verification process.
* Upon successful verification, the platform will assign a unique Merchant ID (MID) to you or your client.

**Endpoint Information**

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/merchants`
* **Authorization Required**: Yes

**Request Parameters**

The request body should include the following fields:**For New Merchant (KYC/KYB)**

```json
{
    "merchantName": "Tom",                // (required, string: Merchant Name (Unique))
    "email": "tom@gmail.com",            // (required, string: Email (Unique))
    "merchantType": "INDIVIDUAL",        // (required, string: Merchant Type [INDIVIDUAL, BUSINESS])
    "callbackUrl": "https://localhost",  // (required, string: URL for KYC/KYB completion callback)
    "languageCode": "en",                // (optional, string: Interface language (en(default)/es/pt/zh))
    "flow": "PROFESSIONALS",             // (optional, KYC flow for INDIVIDUAL only: [PROFESSIONALS(default), CONSUMERS])
    "remark": "test",                    // (optional, string: Remark)
    "industryType": "",                  // (required, enum: payment_psp/fintech/lending/fx_or_otc/e-commerce/gaming_or_entertainment/crypto_or_web3/supply_chain/import_or_export/payroll_or_hr/media_or_advertising/remittance_or_money_transfer/treasury_or_asset_management/wholesale_or_b2b_marketplace/logistics_and_courier/digital_content_or_streaming/travel_or_booking/online_marketplace/investment_and_crowdfunding/real_estate_and_proptech/accounting_or_billing/freelancer_platform/saas_or_api/online_education/outsourcing_agency/other)
    "industryTypeRemark": ""             // (optional, required if industryType = "other")
}

```

**For Unverified Merchant**

```json
{
    "merchantId": 15126673, //(required, number: id of the merchant)
    "callbackUrl": "https://localhost", //(required, string: URL for KYC/KYB completion callback)
    "languageCode": "en" //(optional, string: Interface language (en(default)/es/pt/zh))
}
```

**Response Structure**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "merchantId": 15126673, //(number: id of the merchant)
        "kycLink": "https://www.velafi.com/verify?velafi_token=abc123" //(string: Link for conducting KYC/KYB verification)
    }
}
```
