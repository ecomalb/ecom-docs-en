# Google Pay™ Documentation

### Step 1: Introduction

Before working with the Google Pay™ API, it is essential to review the official documentation. It contains service usage requirements, integration guidelines, and a checklist for verifying the correctness of the connection.

1. **For mobile app developers**: Includes information on Google Pay™ API usage rules, Google Pay™ branding,[ user guides](https://developers.google.com/pay/api/web/guides/brand-guidelines), and an[ integration checklist](https://developers.google.com/pay/api/android/guides/test-and-deploy/integration-checklist).
2. [**For website developers**](https://developers.google.com/pay/api/web/overview?authuser=0): Covers guidelines for applying the Google Pay™ API and its branded elements, [user guides](https://developers.google.com/pay/api/web/guides/brand-guidelines), and an [integration checklist](https://developers.google.com/pay/api/android/guides/test-and-deploy/integration-checklist).

[To properly integrate the Google Pay™ API and receive `PaymentData`](https://developers.google.com/pay/api/web/guides/tutorial?authuser=0) in your website or application, ensure the following:

* Use a web page with the HTTPS protocol and a valid TLS certificate.
*   Configure the following parameters:

    ```json
    {
      "allowPaymentMethods": "CARD",
      "tokenizationSpecification": { "type": "PAYMENT_GATEWAY" },
      "allowedCardNetworks": ["MASTERCARD", "VISA"],
      "allowedCardAuthMethods": ["PAN_ONLY", "CRYPTOGRAM_3DS"],
      "gateway": "timeproject",
      "gatewayMerchantId": "<your_unique_merchant_id>"
    }
    ```
* The `gatewayMerchantId` is a unique store identifier assigned when connecting to the Alliance Bank payment gateway.
* **3DS verification** for `PAN_ONLY` is enabled by default.

### **Step 2: Integrating Your Website or App with Google Pay™ API and the Alliance Bank Payment Gateway**

If the integration is successful, a payment button will appear on your website or app. When clicked, the user will see a pop-up window displaying a list of their Google™ account-linked payment cards.

Example parameters returned by the Google Pay™ API can be found in the [**Payment Processing Request**](https://docs.merchant.alb.ua/en/payment-methods-h2h/googlepay-tm-encrypted/payment-request) documentation.

### **Step 3: Activating Google Pay™ as a Payment Method for Merchants and Users**

* If your online store is already integrated with **Alliance Bank**, contact your account manager or send a request to **`ecom.support@bankalliance.ua`**.
* If integration with **Alliance Bank** has not yet been completed, also contact the specified email address **`ecom.support@bankalliance.ua`**.

### **Step 4: Processing Data from the "token" Parameter**

There are two methods for processing the received token:

1. **Decryption on the merchant's side** – The data is decrypted before being sent to Alliance Bank.
2. **Decryption on the Alliance Bank side** – The data is transmitted in its original form to Alliance Bank.

For decrypting [`paymentData`](https://developers.google.com/pay/api/web/guides/tutorial), Google™ recommends using the [**Tink** ](https://github.com/tink-crypto/tink)library.

Refer to the [**Tink Library Usage Guide**](https://developers.google.com/pay/api/processors/guides/implementation/using-tink) for details.

### **Step 5: Verify Integration Compliance Using the Checklist**

* Review the [**integration checklist**](https://developers.google.com/pay/api/web/guides/test-and-deploy/integration-checklist) to ensure all steps for the payment page integration are completed.
* Ensure the **Android app** [**integration**](https://developers.google.com/pay/api/web/guides/test-and-deploy/integration-checklist) meets all requirements.

### **Step 6: Request Access to the Live Version from Google™ Specialists**

* Submit a **live access request** for [your website](https://developers.google.com/pay/api/web/guides/test-and-deploy/publish-your-integration).
* Submit a **live access request** for your [Android app](https://developers.google.com/pay/api/android/guides/test-and-deploy/publish-your-integration).

***

***

