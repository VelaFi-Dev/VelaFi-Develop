---
icon: circle-exclamation
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/V9hKdCChTHquQ6LtTGc9/error-reference/error-and-warning-dictionary
---

# Error and Warning Dictionary

***

\
**Parameter Errors**

| Code  | Message                           | Description                                        |
| ----- | --------------------------------- | -------------------------------------------------- |
| -4010 | PARAM\_IS\_INVALID                | Parameter {0} is invalid                           |
| -4011 | PARAM\_EXCEEDS\_LIMIT\_LENGTH     | Parameter {0} exceeds the limit length of {1}      |
| -4012 | PARAM\_EXCEEDS\_LIMIT\_QUANTITY   | Parameter {0} exceeds the limit quantity of {1}    |
| -4013 | PARAM\_MUST\_LENGTH\_CHAR         | The length of parameter {0} must be {1} characters |
| -4014 | PARAM\_MUST\_LENGTH\_LETTERS      | The length of parameter {0} must be {1} letters    |
| -4015 | PARAM\_MUST\_LENGTH\_NUMERIC      | The length of parameter {0} must be {1} digits     |
| -4016 | PARAM\_MUST\_POSITION             | The parameter {0} must be {1} at position {2}      |
| -4021 | PARAM\_NOT\_IS\_NUMERIC           | Parameter {0} is not numeric type                  |
| -4022 | PARAM\_NOT\_IS\_ALPHABETIC        | Parameter {0} is not alphabetic type               |
| -4023 | PARAM\_NOT\_IS\_ALPHANUMERIC      | Parameter {0} is not alphanumeric type             |
| -4024 | PARAM\_IS\_INVALID\_ISO1          | Parameter {0} is an invalid ISO 3166-1 code        |
| -4025 | PARAM\_IS\_INVALID\_ISO2          | Parameter {0} is an invalid ISO 3166-2 code        |
| -4026 | PARAM\_IS\_INVALID\_ACCOUNT\_TYPE | Parameter {0} is an invalid account owner type     |
| -4040 | COMMON\_ERROR\_CODE               | fill with unknown errors                           |
| -4041 | COMMON\_TRAN\_CODE                | fill with unknown errors                           |
| -1174 | REPEATED\_SUBMIT\_REQUEST         | Repeated submit request                            |

#### **Payment Method Errors**

| Code  | Message                               | Description                                                                   |
| ----- | ------------------------------------- | ----------------------------------------------------------------------------- |
| -4027 | PAYMENT\_NOT\_EXIST                   | The payment method doesn't exist                                              |
| -5001 | PAYMENT\_SELECT\_AUTO                 | Please select automatic payment method                                        |
| -5002 | PAYMENT\_NOT\_ACCOUNT\_INFO           | Payment method has no bank account information                                |
| -5003 | PAYMENT\_NOT\_EDIT                    | Payment method cannot be modified temporarily                                 |
| -5004 | PAYMENT\_NOT\_CONFIG\_AUTO\_API       | Payment method does not have automatic bank API configured                    |
| -5014 | PAYMENT\_ACCOUNT\_INFO\_AND\_MC\_SAME | Bank card information matches merchant's card information                     |
| -5017 | PAYMENT\_INVALID                      | Invalid payment method                                                        |
| -5018 | PAYMENT\_AND\_PLATFORM\_NOT\_MATCH    | Payment method does not match the platform configuration, please choose again |
| -5048 | PAYMENT\_TYPE\_INVALID                | The payment type is invalid                                                   |
| -5053 | PAYMENT\_ACCOUNT\_ALREADY\_EXISTS     | Account already exists                                                        |
| -5054 | PAYMENT\_ADD\_FAIL                    | Failed to add a payment method; please edit and resubmit                      |
| -2017 | EMAIL\_EXIST                          | The email already exists                                                      |

***

#### **Merchant Errors**

| Code  | Message                                | Description                                                       |
| ----- | -------------------------------------- | ----------------------------------------------------------------- |
| -5005 | MC\_EXIST                              | Merchant already exists                                           |
| -5006 | MC\_NOT\_EXIST                         | Merchant does not exist                                           |
| -5007 | MC\_INVALID                            | Invalid merchant information                                      |
| -5015 | CUIT\_AND\_MC\_NOT\_MATCH              | The CUIT does not match with your selected merchant               |
| -5038 | MC\_ACCOUNT\_NOT\_EXIST                | The merchant account does not exist                               |
| -5039 | MC\_SETTINGS\_EXIST                    | The merchant settings do not exist                                |
| -5056 | PAYMENT\_AND\_MC\_SETTINGS\_NOT\_MATCH | Payment information doesn't match merchant configuration          |
| -5059 | MC\_REGISTER\_FAIL                     | Merchant registration failed                                      |
| -5064 | EXCEEDED\_MC\_NUMBER                   | Exceeded the maximum number of merchants (max: {0})               |
| -5065 | MC\_ACCOUNT\_INVALID                   | The merchant channel is invalid                                   |
| -5066 | MC\_ACCOUNT\_REVIEWING                 | The merchant's account is under verification                      |
| -5067 | MC\_ACCOUNT\_END                       | The merchant account certification process has ended              |
| -5069 | MC\_NAME\_EXIST                        | The merchant name already exists                                  |
| -5070 | MC\_NOT\_OPEN\_ACCOUNT                 | The merchant has not activated the automatic mode account for {0} |
| -5071 | MC\_CHANNEL\_INVALID                   | Merchant channel is invalid                                       |

***

#### **Order Errors**

| Code  | Message                              | Description                                                                 |
| ----- | ------------------------------------ | --------------------------------------------------------------------------- |
| -5008 | ORDER\_REFUND\_NOT\_OP               | Refund orders cannot be processed                                           |
| -5009 | ORDER\_PAYING                        | Order is in payment process; current operation unavailable                  |
| -5010 | ORDER\_AUTO\_NOT\_MANUAL\_COMPLETE   | Automated orders cannot be completed manually                               |
| -5011 | ORDER\_AUTO\_NOT\_CURRENT\_OPERATION | Automated orders cannot perform current operation                           |
| -5034 | ORDER\_END                           | The order process is over                                                   |
| -5035 | ORDER\_NOT\_FINISH                   | Orders cannot be filled at present                                          |
| -5041 | ORDER\_UNPAID\_CAN\_UPLOAD           | Only non-payment or pending-document orders can upload supporting documents |
| -5050 | ORDER\_MIN\_AMOUNT                   | Order does not meet the minimum limit (min {0} {1})                         |
| -5060 | ORDER\_MAX\_AMOUNT                   | Order does not meet the maximum limit (max {0} {1})                         |

***

#### **Trading Pair Errors**

| Code  | Message                               | Description                                               |
| ----- | ------------------------------------- | --------------------------------------------------------- |
| -5019 | SYMBOL\_INVALID                       | Invalid trading pair                                      |
| -5020 | SYMBOL\_BUY\_CLOSED                   | BUY direction is closed                                   |
| -5021 | SYMBOL\_SELL\_CLOSED                  | SELL direction is closed                                  |
| -5045 | FIAT\_INVALID                         | Invalid fiat                                              |
| -5047 | SYMBOL\_AND\_PAYMENT\_NOT\_MATCH      | The symbol does not match the payment method              |
| -5051 | PAYMENT\_FIAT\_AND\_ORDER\_NOT\_MATCH | Fiat currency in payment method does not match order fiat |
| -5057 | COUNTRY\_AND\_FIAT\_NOT\_SUPPORT      | The selected country and fiat currency are not supported  |
| -5058 | TOKEN\_NOT\_SUPPORT                   | The selected crypto is not supported                      |

***

#### **Risk Control Errors**

| Code  | Message                     | Description                                            |
| ----- | --------------------------- | ------------------------------------------------------ |
| -5022 | PRICE\_BELOW\_SAFE          | Price is below the trade line                          |
| -5023 | BASE\_RATE\_CONFIG\_INVALID | The current coin pair is not supported                 |
| -5024 | USER\_RATE\_CONFIG\_INVALID | Invalid user rate configuration; contact admin         |
| -5025 | RISK\_RATE\_CONFIG\_INVALID | Invalid risk control rate configuration; contact admin |
| -5027 | RATE\_INVALID               | Current exchange rate is invalid                       |

***

#### **KYC/KYB Errors**

| Code  | Message                                | Description                                         |
| ----- | -------------------------------------- | --------------------------------------------------- |
| -5032 | NOT\_WHITELIST\_USER                   | Not an OTC whitelist user; contact customer service |
| -5033 | NOT\_API\_USER                         | Not an API user; contact customer service           |
| -5037 | NEED\_UPLOAD\_DOCUMENTS                | You need to upload supporting documents             |
| -5042 | USER\_NOT\_UPLOAD\_DOCUMENTS           | No supporting documents were uploaded               |
| -5043 | NEED\_PASS\_KYC\_OR\_KYB               | You must pass KYC/KYB to perform this operation     |
| -5044 | PAYMENT\_ADD\_NEED\_PASS\_KYC\_OR\_KYB | You must pass KYC/KYB to add this payment method    |
| -5055 | KYC\_OR\_KYB\_REGISTER\_FAIL           | KYC/KYB registration failed                         |
| -5061 | MAX\_DOCUMENT                          | Exceeded maximum uploadable documents (max {0})     |
| -5062 | MC\_KYC\_REVIEWING                     | Merchant KYC is under verification                  |
| -5063 | MC\_KYC\_END                           | Merchant KYC certification process has ended        |

***

#### **Compliance Errors**

| Code  | Message                                    | Description                                                           |
| ----- | ------------------------------------------ | --------------------------------------------------------------------- |
| -5012 | BANK\_NOT\_SUPPORT                         | Bank not supported                                                    |
| -5013 | MC\_COUNTRY\_NOT\_SUPPORT                  | Automatic API is not supported in this country                        |
| -5016 | FIAT\_NOT\_MATCH                           | The fiat currency does not match the merchant                         |
| -5026 | PEND\_ORDER\_NUM\_LIMIT                    | Too many pending orders (current: {0}); wait before creating new ones |
| -5028 | SELF\_ORDER\_CLOSE                         | Self-service ordering is temporarily closed                           |
| -5029 | ORDER\_UID\_EXCEED\_LIMIT                  | Order exceeds user's monthly transaction limit                        |
| -5030 | ORDER\_MC\_EXCEED\_LIMIT                   | Order exceeds user's monthly limit with the merchant                  |
| -5031 | TRADE\_TEMP\_NOT\_PROCEED                  | Transaction temporarily unavailable; contact support                  |
| -5036 | PAYMENT\_FEE\_INVALID                      | Fee config invalid; contact support                                   |
| -5046 | COMMON\_ERROR                              | Please try again or contact customer service                          |
| -5049 | CONFIG\_INVALID                            | Invalid config                                                        |
| -5052 | DESELECT\_MC                               | Merchant selection is not available for manual payment methods        |
| -5068 | NOT\_RELIANCE\_MODE                        | You are not a Reliance model user; function unavailable               |
| -5072 | ACCOUNT\_TYPE\_AND\_BANK\_CODE\_NOT\_MATCH | Account type \[{0}] does not support bank code \[{1}]                 |

<br>
