---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/changelog/changelog
---

# 🕕 Changelog

***

### VelaFi API Documentation V2

***

**Release Date: 2025-11-18**

***

**Guides**

#### **1. Step-by-Step Guide**

* Updated the onboarding workflow description to improve clarity and reflect the latest merchant setup process.

#### **2. Creating Your Merchant**

* Updated the KYC/KYB merchant creation process, including clearer guidance on verification steps and requirements.

#### **3. Activate Merchant Account**

* Updated the merchant account activation flow, with clearer explanation of fiat account activation requirements.

#### **4. Limits (New Guide)**

* Added a new guide introducing merchant limit levels, approval criteria, and instructions on requesting limit upgrades.

***

**API Reference**

#### **5. Account – Get Account Details**

* Updated the API response structure to include merchant limit information and related fields.

#### **6. Merchant – Create Merchant**

* Updated the KYC/KYB workflow for merchant creation.
* Added improved API request and response examples.

#### **7. Merchant – Get a List of Merchants**

* Updated API fields related to merchant limits, including limit status and approval/rejection reasons.

#### **8. Merchant – Activate Merchant Account (Individual)**

* Updated the activation flow for individual merchants’ fiat accounts.

#### **9. Merchant – Activate Merchant Account (Business)**

* Updated the activation flow for business merchants’ fiat accounts with refined workflow requirements.

#### **10. Merchant – Get a List of Merchant Accounts**

* Updated API response fields related to merchant account limits and limit status tracking.

#### **11. Merchant – Upgrade Merchant Limit**

* Updated the merchant limit upgrade process with revised approval logic and enhanced parameter definitions.\
  <br>

***

**Release Date: 2025-06-13**

***

#### 1. Workflow Update: Merchant Creation Process

[Guides – Creating Your Merchant](../guides/creating-your-merchant.md)\
The merchant creation process has been updated to adopt the KYC/KYB model.

> **Note:** Endpoints prior to 2025-06-13 will remain functional for the time being, but support will be deprecated at a later date. Users are encouraged to migrate to the new flow promptly.

#### 2. API Update: Create Merchant Endpoint

[API Reference – Create Merchant](../api-reference/merchant/create-merchant.md)\
The `create merchants` API endpoint has been updated to align with the new KYC/KYB process.

> **Note:** Existing endpoint versions released before 2025-06-13 will continue to work temporarily, but deprecation is planned.

#### 3. New Feature: Activate Merchant Account (Guide)

[Guides – Activate a Merchant Account](../api-reference/merchant/activate-merchant-account-for-individual.md)\
A new step has been added to allow users to **activate fiat accounts** once a merchant entity is successfully created. This ensures the merchant is fully operational in terms of fiat transactions.

#### 4. New API Endpoint: Activate Merchant Account

[API Reference – Activate Merchant Account<br>](../api-reference/merchant/activate-merchant-account-for-individual.md)Introduces a new API endpoint that enables merchants to **activate their fiat account** after the initial merchant setup is complete. This ensures the merchant is fully operational in terms of fiat transactions.

***

**Release Date: 2025-05-08**

***

**1.Funding Records Message Push Webhook**\
This update aims to provide more detailed funding record information for better tracking and management of fund sources.

* **Request Body Parameters**:
  * **New Fields**:
    * `payerName`: string: name of the entity sending funds
    * `payerAccount`: string: bank account of the entity sending funds

**2.** **Added API endpoint** `/v2/merchant/transfer` for internal fund transfers.

***



**Release Date: 2025-04-14**

This version introduces new API endpoints and webhook functionality related to the Pending Fund system, as well as updates to available payment methods.

***

#### 1. Payment Method Update in Guides

* **New Payment ID: 70 – VelaFi Pending Fund**\
  When creating an order via API, users can now select **VelaFi Pending Fund** as the payment or receiving method. This enables faster transaction processing by utilizing preloaded funds.

***

#### 2. New API Endpoint: Retrieve Pending Fund

**Location**: API Reference > Merchant

* Allows users to query their **Pending Fund account** via API.
* Enables users to preload funds into the account, avoiding delays from external transfer confirmation during transactions.

***

#### 3. New API Endpoint: Claim Pending Fund

**Location**: API Reference > Merchant

* Enables withdrawal of available balances from the **Pending Fund account** to a specified payment method.
* Withdrawals are available at any time, allowing flexible fund management.

***

#### 4. New API Endpoint: Retrieve Funding Records

**Location**: API Reference > Merchant

* Provides detailed records of all **Pending Fund-related activities**, including deposits, withdrawals, usage, and refunds.
* Supports full traceability and financial transparency.

***

#### 5. New Webhook: Funding Records Message Push

**Location**: Webhooks

* Introduces webhook notifications for **Pending Fund events**.
* Merchants receive real-time updates with structured transaction data, improving operational automation and monitoring.

***
