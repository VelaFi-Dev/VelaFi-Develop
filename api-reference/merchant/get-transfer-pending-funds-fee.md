---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/merchant/get-transfer-pending-funds-fee
---

# Get Transfer Pending Funds Fee

This endpoint can obtain the transaction fees for inter-merchant transfers. The fee models include fixed fee and percentage fee.



Endpoint Information

* Request Header: `X-BH-TOKEN: ******`
* Request Method: `GET`
* Request Path: `/v2/merchant/transfer_fee`
* Authorization Required: Yes

\
Parameters

* `fiat`: (Required, String) - Fiat currency, Currently supports MXN and ARS

#### Response Structure

The response will return the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {        
        "fiat": "MXN",     //string: Fiat currency         
        "feeType": 1,      //int: Transfer fee type [0: Fixed fee, 1: Percentage fee]
        "fee": 0.01,       //decimal: Transfer fee value (in percentage format, the range is from 0 to 1) 
    }
}
```

#### Example Response (Fixed)

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {        
        "fiat": "MXN",
        "feeType": 1, 
        "fee": 0.01,
    }
}
```

#### Example Response (Percentage)

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {        
        "fiat": "MXN",
        "feeType": 0,
        "fee": 5,
    }
}
```

#### Notes

* Supported Fiat Currencie&#x73;**:** Currently supports MXN (Mexican Peso) and ARS (Argentine Peso).
* The `feeType` There are two types of this:
  * Fixed Fee (`feeType=0`): A set flat rate applied to each transaction.
  * Percentage Fee (`feeType=1`): A variable fee calculated as a percentage of the transfer amount.
