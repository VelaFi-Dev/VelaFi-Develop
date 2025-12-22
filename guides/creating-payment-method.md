---
icon: basket-shopping-minus
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/guides/creating-payment-method
---

# Creating Payment Method

This guide provides detailed information about managing payment methods, including how to retrieve payment method templates and add new payment methods.&#x20;

## **I. Get Payment Method Templates**

#### Endpoint Information

* **Request Method**: `GET`
* **Request Header**: `X-BH-TOKEN: ******`
* **Request Path**: `/v2/payments/templates`
* **Authorization Required**: Yes



#### Request Parameters

**Query Parameters**

| Parameter | Type   | Required | Description              |
| --------- | ------ | -------- | ------------------------ |
| paymentId | number | Yes      | ID of the payment method |

#### Response Structure

The response will contain the following fields:

```json
{
  "code": 0,
  "msg": "",
  "data": {
      [string]: [string]
  }
}
```

#### Example Responses

**Payment Type 1: Bank Information**

**Mexico Bank**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "CLABE number": "",
        "Account number/card": "",
        "Beneficiary Name": ""
    }
}
```

**Argentina Bank**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "CVU number": "",
        "cuit": "",
        "Bank name": ""
    }
}
```

**Payment Type 2: SEPA  Transfers**

**SEPA**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Bank Name": "",
        "Account Owner Name": "",
        "Account Owner Type": "",
        "Bank Country/Region": "",
        "Account Number": "",
        "Bic": "",
        "firstName": "",
        "lastName": "",
        "businessName": ""
    }
}

Account Owner Type must be either Business or Individual.
If Account Owner Type is Business, businessName is required.
If Account Owner Type is Individual, firstName and lastName are required.
Bank Country/Region is ISO 3166-1

```

**WIRE / ACH Transfers**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Bank Name": "",
        "Account Owner Name": "",
        "Account Owner Type": "",
        "Bank Country/Region": "",
        "Account Number": "",
        "Routing Number": "",
        "Street Line1": "",
        "Street Line2": "",
        "City": "",
        "State": "",
        "Postal Code": "",
        "firstName": "",
        "lastName": "",
        "businessName": ""
    }
}

Account Owner Type must be either Business or Individual.
If Account Owner Type is Business, businessName is required.
If Account Owner Type is Individual, firstName and lastName are required.
Bank Country/Region is ISO 3166-1
State is ISO 3166-2
```

**Payment Type 3: SWIFT / CHATS**

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "Account Owner Type": "",
        "IBAN": "",
        "Bank Name": "",
        "Bank Country/Region": "",
        "Bank Identifier": "",
        "Street": "",
        "City": "",
        "State": "",
        "Country/Region": "",
        "Postal Code": ""
        "firstName": "",
        "lastName": "",
        "businessName": ""
    }
}

Account Owner Type must be either Business or Individual.
If Account Owner Type is Business, businessName is required.
If Account Owner Type is Individual, firstName and lastName are required.

Bank Country/Region is ISO 3166-1

```

## **II. Add Payment Method**

#### Endpoint Information

* **Request Method**: `POST`
* **Request Path**: `/v2/payments`
* **Request Header**: `X-BH-TOKEN: ******`
* **Authorization Required**: Yes



#### Request Parameters

**Request Body**

The request body should include the following parameters:

| Parameter  | Type   | Required | Description                                                         |
| ---------- | ------ | -------- | ------------------------------------------------------------------- |
| merchantId | number | Yes      | ID of the merchant id                                               |
| paymentId  | number | Yes      | ID of the payment method                                            |
| country    | string | Yes      | Name of the country                                                 |
| fiat       | string | Yes      | Name of the fiat currency                                           |
| realName   | string | No       | Real name of the account holder                                     |
| fieldJson  | object | Yes      | Field JSON of the payment template, format `{ [string]: [string] }` |
| remark     | string | No       | Additional remarks for the payment method                           |

**Request Example**

```json
{
  "merchantId": 0,
  "paymentId": 0,
  "country": "",
  "fiat": "",
  "realName": "",
  "fieldJson": {
      "fieldName": "value"
  },
  "remark": ""
}
```

#### Response Structure

The response will contain the following fields:

```json
{
  "code": 0,
  "msg": "",
  "data": {
      "id": 0,  // User payment ID
      "status": 0, // Status: [1: valid, 2: authenticating, 3: authentication failed]
      "failReason": "" // Reason for authentication failure
  }
}
```

### Notes

* Ensure to provide valid parameters for successful creation of payment methods.
* The `merchantId` and `paymentId` must correspond to existing configurations in the system.
* Pay attention to the status and failure reason in the response for troubleshooting.
