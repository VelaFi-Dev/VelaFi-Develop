---
icon: people-pants
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/guides/creating-your-merchant
---

# Creating Your Merchant

This section describes how to create a compliant individual or business entity (Merchant) under the **VelaFi compliance framework**. You will initiate the **KYC/KYB verification process**, receive a redirect URL for user verification, and learn about the available merchant management modes.

### Overview

To operate within VelaFi’s regulated ecosystem, every merchant must complete **Know Your Customer (KYC)** or **Know Your Business (KYB)** verification.When creating a merchant via API, you must submit detailed business or personal information to initiate the compliance review.Once the verification is successful, the platform will assign a **unique Merchant ID (MID)** to you or your client. This `MID` is required for all subsequent API calls related to transactions, account management, and settlements.

***

### KYC/KYB Verification Flow

When the API request for merchant creation is successful, the response will include a **unique redirect URL**. This URL leads to VelaFi’s secure KYC/KYB verification page.You can choose between two integration options:

* **Redirect Mode** — Directly redirect your user to the provided URL to complete the verification process.
* **Embedded Mode** — Embed the verification page into your front-end application using an `<iframe>` for a seamless user experience.

> ⚠️ **Important:** The verification URL may expire or become invalid after a specific period, depending on session and configuration settings. Ensure it is used promptly.

***

### Merchant Management Modes

VelaFi provides two operational models for merchant creation and management:

#### 1.Multi-Merchant Management

Once your **primary merchant account** has successfully passed KYB verification, you can create and manage **sub-merchants** (either individuals or entities) under your account. This enables **hierarchical merchant management**, along with flexible **role-based access control** and configuration.Typical use cases include:

* Aggregators managing multiple clients
* Platforms offering payment infrastructure to sub-merchants
* Marketplace operators handling merchant-level compliance separately

***

#### 2.Reliance Mode (Optional)

If you are a **licensed financial institution**, you can apply to enable **Reliance Mode**. This mode grants you greater autonomy over merchant operations and compliance.In Reliance Mode:

* You are responsible for merchant onboarding, review, and ongoing compliance monitoring.
* VelaFi does **not** intervene in your merchant onboarding workflow.
* VelaFi provides the **technical infrastructure**, **settlement rails**, and **regulatory support** to ensure transactions remain secure, efficient, and compliant.

> 🛡️ Reliance Mode requires an additional compliance review by the VelaFi Compliance Team.

[Click here ](https://velafi.notion.site/Reliance-Model-Onboarding-Guide-With-TruBit-2944850302de80619bb8daa72f3a8841)to learn more about the Reliance Mode application process.

