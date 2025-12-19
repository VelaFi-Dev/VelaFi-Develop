---
icon: box
metaLinks:
  alternates:
    - https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/guides/sandbox
---

# Sandbox

VelaFi offers a **sandbox environment** designed to facilitate rapid integration testing without the necessity of using real funds. The sandbox can be accessed at:

* **Sandbox URL**: \
  [`https://api-test.velafi.com`](https://api-test.velafi.com)

For instance, to retrieve information about fiat trading pairs, you can utilize the following endpoint:

* **Fiat Trading Pairs Endpoint**: \
  [`https://api-test.velafi.com/v2/base/fiat/symbols`](https://api-test.velafi.com/v2/base/fiat/symbols)

#### Sandbox API Credentials

To access the sandbox environment, use the following credentials:

*   **API Key**:

    ```
    Please contact the VelaFi team to get it.
    ```
*   **API Secret**:

    ```
    Please contact the VelaFi team to get it.
    ```

#### Key Differences Between Sandbox and Production Environments

We recommend utilizing the sandbox environment exclusively for testing API request/response behaviors, while reserving the production environment for all other types of testing activities.

**Distinctions:**

1. **No KYC Registration or API Key Creation Required**:\
   The sandbox environment eliminates the need for actual identity verification and API key generation.
2. **Virtual User and Account Data**:\
   All user and account information within the sandbox is simulated and not linked to real individuals.
3. **No Actual Fund Transfers**:\
   The sandbox environment does not facilitate real financial transactions; all processes are entirely simulated.
4. **Webhook Callbacks Are Not Triggered**:\
   In the sandbox environment, webhooks will not initiate any callback events.

#### Conclusion

We encourage you to leverage the sandbox environment thoroughly to validate your integration before deploying it in the production environment. This ensures that your application functions as intended and minimizes the risk of issues in a live setting.
