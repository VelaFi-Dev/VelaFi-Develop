# Open Merchant Virtual Account

This endpoint enables merchants to open multiple virtual accounts. The prerequisite for this is the already activated merchant's corresponding fiat currency account. Currently, the supported fiat currencies are MXN, ARS, BRL, and COP.

#### Endpoint Information

* **Request Header**: `X-BH-TOKEN: ******`
* **Request Header**: `Content-Type: application/json`
* **Request Method**: `POST`
* **Request Path**: `/v2/merchant/virtual/accounts`
* **Authorization Required**: Yes



**Request Parameters**The request body should include the following fields:

```json
{     
    "merchantId": 151209, //(required, string: Merchant id)  
    "fiat": "MXN", // (required, string: name of the fiat currency [MXN,ARS,BRL,COP])  
    "paymentId": 58,  // (required, number: id of the payment [58=MXN/105=MXN,63=ARS,68=COP,90=BRL]) 
    "alias": "alias" //(required, string: alias, The combination of merchantId, fiat, paymentId and alias is unique. 
                     //The value of alias can only consist of letters and numbers.) 
}
```

**Response Structure**The response will include the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": {
        "fiat": "MXN", //(string: name of the fiat currency)
        "status": 2 //(number: The status of the virtual account [1: authenticating, 2: normal, 3: authentication failed])       
    }
}
```

#### Notes

* Ensure that all fields in the request body are filled out correctly to facilitate the activation process.
* Merchants may need to provide additional documentation based on the type of account being activated.
