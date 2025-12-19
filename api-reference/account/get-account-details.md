---
description: Account
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/account/get-account-details
---

# Get Account Details

This API retrieves the basic account information associated with the authenticated user, including company details, country, KYC status, and monthly usage limits.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Method**: `GET`
* **Request Path**: `/v2/user/account`
* **Authorization Required**: Yes



#### Response Structure

The response will include the following fields:

```json
{
  "code": 200,                      // (number: response code)
  "msg": "SUCCESS",                 // (string: message)
  "data": {                         // (object: account details)
    "userId": 0,                    // (number: user ID)
    "country": "",                  // (string: name of the country)
    "companyName": "",              // (string: name of the company)
    "kycPassed": false,             // (boolean: whether the user passed KYC)
    "monthLimit": 25000.0,          // (number: month amount limit)
    "monthUsed": 0.0                // (number: month amount used)   
  }
}
```

**Example Response**

```json
{
  "code": 200,
  "msg": "SUCCESS",
  "data": {
    "userId": 1,
    "country": "Argentina",
    "companyName": "velafi",
    "kycPassed": true,
    "monthLimit": 250000.0,
    "monthUsed": 0.0
  }
}
```

####

#### Notes

* Ensure that you include the necessary authorization tokens in the request headers for successful execution.
* The `kycPassed` field indicates whether the user has completed the KYC (Know Your Customer) process.
