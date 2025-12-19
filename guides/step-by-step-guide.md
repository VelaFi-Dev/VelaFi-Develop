---
description: Guide
icon: book-open-reader
metaLinks:
  alternates:
    - https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/guides/step-by-step-guide
---

# Step-by-Step Guide

### Onboarding with **VelaFi**&#x20;

This section walks you through the complete onboarding process with VelaFi, including account registration, API key generation, merchant setup, compliance verification, and payment accout activation.



1. [**Creating VelaFi Account**](creating-velafi-account.md)\
   Begin by registering an account on the VelaFi Platform. Upon successful registration, the system will assign a unique **User ID (UID)**, which serves as the identifier for managing all your transactions, merchants, API, and account-level operations.<br>
2.  [**Create a Merchant & Complete Compliance Verification (KYC/KYB)**](creating-your-merchant.md)

    To operate under VelaFi’s compliance framework, you must create a legal individual or business entity (Merchant).

    * Submit detailed merchant information to initiate the KYC/KYB verification process.
    * Once approved, the platform will assign a unique **Merchant ID (MID)** to you or your client.
    * Upon successful creation, a **crypto custody wallet** will be automatically provisioned for the merchant with an initial monthly withdrawal limit of **USD 15,000.**


3.  [**Create API Key**](creating-api-key/)\
    Once your account is activated, log in to the VelaFi dashboard to generate your **API Key**. This key is required to authenticate your API requests and securely interact with VelaFi’s services.\
    \
    **Environment Selection**

    | Environment | Base URL                                                   | Description                                 |
    | ----------- | ---------------------------------------------------------- | ------------------------------------------- |
    | Sandbox     | [https://api-test.velafi.com](https://api-test.velafi.com) | Test environment for simulated transactions |
    | Production  | [https://api.velafi.com](https://api.velafi.com)           | Live environment for real transactions      |



4. [**API Access Activation**](https://share.hsforms.com/10CFW-gfVR3GvDmNX6r8M6wr8y9l)

After generating your API key, please contact the **VelaFi Support Team** to enable API access for your account.

> **Email:** contact@velafi.com



5\. [**Activate Merchant Payment Account**](activate-merchant-account.md)

Submit the required documents and information for the target countries where your merchant will operate to activate fiat channels (e.g., ARS, MXN, BRL, PEN, COP, USD, etc.).

> [**Activate Merchant Account (For Individual)**](../api-reference/merchant/activate-merchant-account-for-individual.md)\
> \
> [**Activate Merchant Account (For Business)**](../api-reference/merchant/activate-merchant-account-for-business.md)

* Each merchant will be assigned a **dedicated payment account**, such as **CVU** and **CUIT** numbers for ARS (Argentina).
* Funds can be deposited into the merchant’s payment account via **bank transfer**.
* VelaFi automatically reconciles incoming payments and credits the corresponding balance to the merchant’s wallet.
* Once activation is complete, you will receive your **monthly transaction limit** for each fiat channel.

[View limits.](limits.md)

> **Need higher limits?** [Click here](../api-reference/merchant/upgrade-merchant-limit.md)

***

### On-Ramp Workflow (Fiat → Crypto)

Review the following Support articles to see our supported currencies and regions for on-ramp:

[View supported cryptocurrencies & fiat currencies](pair.md)<br>

#### 1. Ensure [Merchant Fiat Account Activation](../api-reference/merchant/activate-merchant-account-for-individual.md)

Before initiating a transaction, please ensure that the merchant has successfully activated their fiat account.\
For example, if Merchant **Alice** wants to perform an **ARS → USDT** transaction, she must first activate her **ARS fiat account**.<br>

#### 2. [Create Fiat to Crypto Order](../api-reference/order/create-a-fiat-to-crypto-order.md)

When an order is created, the system will generate a unique `order_id` to track the transaction.

#### 3. [Retrieve a Specific Order](../api-reference/order/retrieve-a-specific-order.md)

To get the details of a specific order, use the `order_id` to query and retrieve comprehensive order information.

#### 4. Make a Payment

There are two payment methods available:

**A. Pending Fund Balance Payment**\
If you select **Merchant Account Pending Fund** and the account balance is sufficient, the system will automatically process the payment.

**B. Real-Time Manual Payment**\
If you opt for **real-time payment**, you must manually transfer the funds to the fiat account specified in the **order details**.

#### 5. System Confirms Order Completion

Once the payment is confirmed, your account will instantly receive the corresponding amount of **cryptocurrency**.



**Note:** Due to compliance requirements, certain transactions may require you to submit supporting documents after order creation via the **Upload Invoice Documents For a Specific Order** endpoint.

***

### Off-Ramp Workflow (Crypto → Fiat)

Review the following Support articles to see our supported currencies and regions for off-ramp:

[View supported cryptocurrencies & fiat currencies](pair.md)<br>

Before initiating a transaction, please ensure that the merchant has successfully activated their fiat account.\
For example, if Merchant Alice wants to perform an **USDT → ARS** transaction, she must first activate her **ARS fiat account And added** [**payment methods**](../api-reference/payment-method/add-payment-method.md)**.**\
<br>

#### 1.[ Create a Crypto to Fiat Order](../api-reference/order/create-a-crypto-to-fiat-order.md)

Initiate a transaction by creating a **Crypto to Fiat** order through the appropriate API endpoint.

#### 2. System Processes the Transaction

Once the order is submitted, the system will handle cryptocurrency validation, conversion, and fiat settlement instructions.

#### 3. Receive Fiat Funds

The fiat currency will be transferred to the beneficiary's account upon successful completion of the transaction.

***

### Global Payment Workflow

Review the following Support articles to see our supported currencies and regions for global payment:

[Supported cryptocurrencies & fiat currencies](pair.md)\
\
\
**Before initiating a transaction, please ensure that the merchant has successfully activated their fiat accounts.**\
For example, if merchant **Alice** intends to perform a **USD → ARS** transaction, she must first activate both her **USD** and **ARS** fiat accounts and add the required payment method.<br>

1. Confirm transfer details:
   * Sender fiat currency & amount
   * Recipient fiat currency & amount
2. Select sender [Merchant](../api-reference/merchant/)
3. Retrieve [payment methods](payment-method-id.md)
4. Select recipient [Merchant](../api-reference/merchant/)
5. Configure recipient [payment method](../api-reference/payment-method/)
6. [Create fiat to fiat order via API](../api-reference/order/create-a-fiat-to-fiat-order.md)
7. Order execution completed
8. Recipient fiat funds received
