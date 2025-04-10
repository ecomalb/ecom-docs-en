# PURCHASE Collection Example

## **1. Authorize by Virtual Device**

**Endpoint:**\
`{{url}}/api-gateway/authorize_virtual_device`

* The request requires a **serviceCode**, which is provided to you before integration into the production environment.
* In response, an **encrypted server key** (`serverPublicKey`) is returned in **JWE format**.
* This key is required for **Step 2**.

## **2. Decrypt Authorization Response**

**Endpoint:**\
`{{url}}/cipher/decrypt_by_jwk?message={{responseJwe}}`

* This request decrypts the bank’s response using the **private key** (`userPrivateKey`).
* The **Merchant** generates this key following the instructions in the "[Client Communication JWK Key Generation Process](https://docs.merchant.alb.ua/en/authentication#process-of-generating-client-communication-jwk-keys)."
* The decrypted **serverPublicKey** obtained in this step is required for **Steps 5 and 8**.
* **In the production environment, the Merchant must perform decryption independently.**

## **3. Encrypt Card Number**

**Endpoint:**\
`{{url}}/cipher/encrypt_by_jwk?message={{card_number}}`

* The **payment key** (`paymentPublicKey`), provided by the **Bank**, is used to encrypt the **customer’s card number**.
* For testing, an auxiliary method `/ecom/help/encrypt_by_jwk` is available.
* **In the production environment, the Merchant must handle encryption independently.**

## **4. Encrypt Expiration Date and CVV**

**Endpoint:**\
`{{url}}/cipher/encrypt_by_jwk?message={{year_month_day}}`

* The **payment key** (`paymentPublicKey`), provided by the **Bank**, is used to encrypt the **card expiration date and CVV**.
* The data should be formatted as: `year, month, CVV` (e.g., `"2603123"`).
* For testing, the auxiliary method `/ecom/help/encrypt_by_jwk` can be used.
* **In the production environment, the Merchant must perform encryption independently.**

## **5. Encrypt Create Purchase Request Body**

**Endpoint:**\
`{{url}}/cipher/encrypt_by_jwk?message={{body_request}}`

* `{{body_request}}` must meet the **mandatory input parameters** for [**PURCHASE Step 1**.](https://docs.merchant.alb.ua/en/payment-methods-h2h/purchase/purchase-request-step-1)
* The **decrypted server key** (`serverPublicKey`) from **Steps 1 and 2** is used to encrypt the purchase request body.
* The response contains the **encrypted request body**: `{{encryptJweT}}`.
* For testing, the auxiliary method `/ecom/help/encrypt_by_jwk` is available.

## **6. Create Purchase Request**

**Endpoint:**\
`{{url}}/ecom/execute_request/payments/v3/create/purchase`

* The request sends the **encrypted request body** (`{{encryptJweT}}`), generated in **Step 5**.
* The response contains an **encrypted response** (`{{responseJwe}}`), required for **Step 7**.

## **7. Decrypt Create Purchase Response**

**Endpoint:**\
`{{url}}/cipher/decrypt_by_jwk?message={{responseJwe}}`

* This request decrypts the bank’s response using the **private key** (`userPrivateKey`).
* The **Merchant** generates this key following the instructions in the "[Client Communication JWK Key Generation Process.](https://docs.merchant.alb.ua/en/authentication#process-of-generating-client-communication-jwk-keys)"
* The response contains the **decrypted response body** from **Step 6**.

## **8. Encrypt Execute Purchase Request Body**

**Endpoint:**\
`{{url}}/cipher/encrypt_by_jwk?message={{body_request}}`

* `{{body_request}}` must meet the **mandatory input parameters** for [**PURCHASE Step** ](https://docs.merchant.alb.ua/en/payment-methods-h2h/purchase/purchase-request-step-2)**2**.
* The **decrypted server key** (`serverPublicKey`) from **Steps 1 and 2** is used to encrypt the purchase execution request body.
* The response contains the **encrypted request body**: `{{encryptJweT}}`.
* For testing, the auxiliary method `/ecom/help/encrypt_by_jwk` is available.

## **9. Execute Purchase Request**

**Endpoint:**\
`{{url}}/ecom/execute_request/payments/v1/execute/purchase`

* The request sends the **encrypted request body** (`{{encryptJweT}}`), generated in **Step 8**.
* The response contains an **encrypted response** (`{{responseJwe}}`), required for **Step 10**.

## **10. Decrypt Execute Purchase Response**

**Endpoint:**\
`{{url}}/cipher/decrypt_by_jwk?message={{responseJwe}}`

* This request decrypts the bank’s response using the **private key** (`userPrivateKey`).
* The **Merchant** generates this key following the instructions in the "[Client Communication JWK Key Generation Process.](https://docs.merchant.alb.ua/en/authentication#process-of-generating-client-communication-jwk-keys)"
* The response contains the **decrypted response body** from **Step 9**.
* For testing, the auxiliary method `/ecom/help/encrypt_by_jwk` can be used.

